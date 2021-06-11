<script>
	import Title from './Title.svelte';
	import SearchBar from '../components/SearchBar.svelte';
	import GenreTab from './GenreTab.svelte';
	import FavoritesTab from './FavoritesTab.svelte';

  	let tabs = ["popular", "Top Rated", "Upcoming"];
  	let selected = tabs[0];
</script>



<nav>
	<Title title="Movie Wiki"/>

	<SearchBar placeholder="Search Movies"/>

	<div class="aside">
		<ul>
			<li>
				<a on:click={()=>selected = tabs[0]} class:selected={selected ==="popular"} >Popular</a>
			</li>
			<li>
				<a on:click={()=>selected = tabs[1]} class:selected={selected ==="Top Rated"} >Top Rated</a>
			</li>
			<li>
				<a on:click={()=>selected = tabs[2]} class:selected={selected ==="Upcoming"} >Upcoming</a>
			</li>
		</ul>
	<div class="seperator"></div>
		<GenreTab />
		<FavoritesTab />
	</div>
</nav>

	{#if selected=== "popular"}
		<p>Popular</p>
	{:else if selected === "Top Rated"}
		<p>top</p>
	{:else}
		<p>up</p>
	{/if}



<style>

	nav{
		font-size: 0.875rem;
		height: 3.1rem;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 0 1.2rem;
		margin: 0 auto;
		box-shadow: 0 1px 2px rgba(0,0,0,0.9),0 0px 2px rgba(0,0,0,0.9);
		user-select: none;
	}
	.seperator{
		background-color: rgba(255, 255, 255, .1);
		height: 1.6rem;
	    width: 1px;
	    margin:0 0.4rem;
	}
	.aside{
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	ul{
		display: flex;
		user-select: none;
	}
	li {
		margin-right: 1rem;
	}
	li:last-child{
		margin-right: 0;
	}
	li a{
		text-transform: capitalize;
		text-align: center;
		padding:0.8rem 0.5rem;
		transition: .01s all;
		cursor: pointer;
	}
	li a.selected{
		color: #a970ff;
		border-bottom: 2px solid #772ce8;
	}
	li a:hover{
		color: #a970ff;
	}
</style>