<script>
	import Loader from '/src/components/Loader.svelte';
	import ClickOutside from 'svelte-click-outside';

		let triggerEl;
    let panelVisible = false;


    function togglePanel() {
      panelVisible = !panelVisible;
    }

    function hidePanel() {
      panelVisible = false;
    }


	let promise = Promise.resolve([]);
	async function fetchUsers() {
		const response = await self.fetch('https://api.themoviedb.org/3/genre/movie/list?api_key=04c35731a5ee918f014970082a0088b1&language=en-US');

		if (response.ok) {
  		return response.json();
			
		} else {
			throw new Error(users);
		}
	}
	promise = fetchUsers();
</script>
<div class="genre-menu">

	<button class="genre {panelVisible ? 'active' : ''}" bind:this={triggerEl} on:click={togglePanel}>
		<span>Genre</span>
		<svg version="1.1" viewBox="0 0 20 20" x="0px" y="0px" class="ScIconSVG-sc-1bgeryd-1 cMQeyU"><g><path d="M14.5 6.5L10 11 5.5 6.5 4 8l6 6 6-6-1.5-1.5z"></path></g></svg>
	</button>
	
	<ClickOutside on:clickoutside={hidePanel} exclude={[triggerEl]}>
    	<div hidden={!panelVisible} class="sub-menu" >

				<div class="submenu-header">

					<p class="sub-menu-title">The Ultimate Movie Genres List</p>

					<div on:click={togglePanel} class="close">
						<svg version="1.1" viewBox="0 0 20 20" x="0px" y="0px" class="ScIconSVG-sc-1bgeryd-1 cMQeyU"><g><path d="M8.5 10L4 5.5 5.5 4 10 8.5 14.5 4 16 5.5 11.5 10l4.5 4.5-1.5 1.5-4.5-4.5L5.5 16 4 14.5 8.5 10z"></path></g></svg>
					</div>

				</div>

					<div class="menu-items" >
							<ul>
								{#await promise}
									<Loader />
								{:then genreArray}
								  {#each genreArray.genres as {name}}
								  	<li on:click={togglePanel}>{name}</li>
								  {/each}
								{:catch error}
									<p style="color: red">{error.message}</p>
								{/await}
							</ul>
					</div>
			</div>
  	</ClickOutside>
</div>


<style>
	.genre-menu{
		position: relative;
		z-index: 200;
	}
	.genre{
		display: flex;
		align-items: center;
		padding:0.5rem 0.6rem;
		border-radius: 0.2rem;
		margin-left: 0.2rem;
		margin-right: 0.5rem;
		background-color: transparent;
		border: none;
		outline:none;
		font-family: inherit;
		font-weight: 600;
		font-size: inherit;
		color: #ffff;
		cursor: pointer;
		transition: 0.1s all;
	}
	.genre:hover,
	.genre.active{
		background-color: rgba(255, 255, 255, 0.2);
	}
	.genre svg,
	.close svg{
		margin-left: 0.5rem;
		width: 1rem;
		height: 1rem;
		text-align: center;
		fill: #ffff;
	}
	.sub-menu-title{
		font-size: 1rem;
	}
	.sub-menu{
		position: absolute;
		top: 2.8rem;
		bottom: 0rem;
		right: 1rem;
		width: 28rem;
		height:30rem;
		border-radius: 0.3rem;
		background-color: #18181b;
		box-shadow: 0 1px 10px #00000080,0 10px 8px #00000066;
		border-bottom: 4px solid #772ce8;
		border-top: 4px solid #772ce8;
	}
	.submenu-header{ 
		min-height: 2.5rem;
	    display: flex;
	    align-items: center;
	    justify-content: space-between;
	    flex-shrink: 0;
	    color: #dedee3;
	    border-top-left-radius: 0.3rem ;
	    border-top-right-radius: 0.3rem ;
	    box-shadow: 0 1px 2px #000000e6,0 0px 2px #000000e6;
	    padding:0 1rem;
	    margin-bottom: 0.2rem;
	}
	.close{
		display: flex;
		align-items: center;
		justify-content: center;
		padding:0.4rem 0;
		border-radius: 0.2rem;
		padding-right: 0.5rem;
		cursor: pointer;
	}
	.close svg{
		width: 1.1rem;
		height: 1.1rem;

	}
	.close:hover{
		background-color: rgba(255, 255, 255, 0.2);
	}
	.genre-count{
		color: #772ce8;
		text-transform: capitalize;
		font-size: 1rem;
		display: flex;
		align-items: center;
		justify-content: center;
		line-height: 17px;
	}
	.genre-count .title{
		color: #efeff1;
		font-size: 0.9rem;
		padding-right: 0.3rem;
	}
	.menu-items{
		overflow-y: auto;
		width: 100%;
		height: auto;
		margin: 0.5rem 0;
	}
	.menu-items ul{
		display: flex;
		align-items: center;
		flex-wrap: wrap;
		padding: 0 0.3rem;
		justify-content: center;
	}
	li{
		display: flex;
		align-items: center;
		justify-content: center;
		width: 7.5rem;
		height: 3.1rem;
		margin: 0.3rem;
		text-align: center;
		background-color: #18181b;
		color: #dedee3;
		padding:0.8rem;
	    box-shadow: 0 1px 1px #000000e6,0 0px 1px #000000e6;
	    border-radius: 0.2rem;
	    cursor: pointer;
	}
	li:hover{
		border-bottom: 4px solid #772ce8;
	}
</style>