<script>
	import Loader from '/src/components/Loader.svelte'
	import SearchBar from '/src/components/SearchBar.svelte'
	import ActorCard from './ActorCard.svelte'
	import ClickOutside from 'svelte-click-outside';

	let triggerEl;
   let panelVisible = false;


   function togglePanel() {
      panelVisible = !panelVisible;
   }

   function hidePanel() {
      panelVisible = false;
   }
	let movieTitle;
	let promise = Promise.resolve([]);
   async function getPopularActors() {
   	const response = await fetch("https://api.themoviedb.org/3/person/popular?api_key=04c35731a5ee918f014970082a0088b1&language=en-US&page=1");
   	if (response.ok) {
  			return response.json();
		} else {
			throw new Error(users);
		}
   }

   promise = getPopularActors();
   
   function getActorMovieList(arr){
   	arr.forEach((item)=>{
   		movieTitle = item.title
   	})
   	return movieTitle
   }
</script>


<section>
	<button bind:this={triggerEl} on:click={togglePanel}  class="pannel-toggle-btn {panelVisible ? 'active' : ''}">
		{#if !panelVisible}
			Trending Actors Across The World &nbsp <svg version="1.1" viewBox="0 0 20 20" x="0px" y="0px" class="ScIconSVG-sc-1bgeryd-1 cMQeyU"><g><path d="M4 16V4H2v12h2zM13 15l-1.5-1.5L14 11H6V9h8l-2.5-2.5L13 5l5 5-5 5z"></path></g></svg>
		{:else}
			<svg version="1.1" viewBox="0 0 20 20" x="0px" y="0px" class="ScIconSVG-sc-1bgeryd-1 cMQeyU"><g><path d="M4 16V4H2v12h2zM13 15l-1.5-1.5L14 11H6V9h8l-2.5-2.5L13 5l5 5-5 5z"></path></g></svg>
		{/if}
	</button>
	<ClickOutside on:clickoutside={hidePanel} exclude={[triggerEl]} class="good">
		<div hidden={!panelVisible} class="container">
				<div class="header">
					<p class="title">Popular Actors</p>
					<SearchBar />
				</div>
				<div class="actors-list-container">
					{#await promise}
						<Loader />
					{:then items}
						{#each items.results as item,index}
							<ActorCard 
									indexNumber="{index+1}" 
									imgSrc="{item.profile_path}"
									name="{item.name}"
									popularityCount="{Math.floor(item.popularity)}"
									moviesList="{getActorMovieList(item.known_for)}" 						
							/>
						{/each}
					{/await}
				</div>
	  		<p class="end-text">This list updates daily</p>
		</div>
	</ClickOutside>
</section>

<style>
	section{
		z-index: 999999;
	}
	.container{
		overflow-y: auto;
		overflow-x: hidden;
		position: absolute;
		top: 0;
		left: 1px;
		transform: translate(0,3.4rem);
		width: 30rem;
		height: 91.5%;
		background-color: #18181b;
		box-shadow: 0 1px 10px #00000080,0 10px 8px #00000066;
		border-bottom: 4px solid #772ce8;
		border-top: 4px solid #772ce8;
	}
	.header{ 
		position: relative;
		height: 6rem;
	    display: flex;
	    align-items: center;
	    justify-content: space-between;
	    flex-direction: column;
	    flex-shrink: 0;
	    color: #dedee3;
	    border-top-left-radius: 0.3rem ;
	    border-top-right-radius: 0.3rem ;
	    padding:0 1rem;
	    margin-bottom: 0.2rem;
	    overflow: hidden;
	}
	.actors-list-container{
		overflow-y: auto;
		overflow-x: hidden;
		margin-top: 1rem;
		padding: 0.5rem 1rem;
		display: inline-flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
	}
	.title{
		position: relative;
		text-transform: uppercase;
		color: #9147ff;
		font-size: 1.5rem;
		margin-top:0.8rem;
	}
	.end-text{
		text-align: center;
		color: #313131;
		font-size: 0.8rem;
		margin-bottom: 0.2rem;
	}
	.pannel-toggle-btn{
		border: 0;
		outline: 0;
		font-family: inherit;
		font-size: inherit;
		display: flex;
		align-items: center;
		justify-content: center;
		position: absolute;
		top: 5rem;
		left: -19rem;
		padding:0.5rem 0.45rem ;
		padding-left: 2rem;
		border-radius: 0.2rem;
		cursor: pointer;
		color: #ffff;
		background-color: rgba(255, 255, 255, 0.3);
		transition: 0.3s left,background-color;
	}
	.pannel-toggle-btn:hover{
		left: -1rem;
		background-color: rgba(255, 255, 255, 0.5);
	}
	.pannel-toggle-btn.active{
		padding:0.5rem 0;
		padding-right: 0.5rem;
		left: 31rem;
		background-color: rgba(255, 255, 255, 0.3);
	}
	.pannel-toggle-btn.active svg{
		margin-left: 0.5rem;
		transform: rotate(180deg);
	}
	.pannel-toggle-btn svg{
		margin-left: 0.7rem;
		width: 1.5rem;
		height: 1.5rem;
		text-align: center;
		fill: #ffff;
	}
	.pannel-toggle-btn svg{
		width: 1.1rem;
		height: 1.1rem;

	}
	.pannel-toggle-btn:hover{
		background-color: rgba(255, 255, 255, 0.2);
	}
</style>