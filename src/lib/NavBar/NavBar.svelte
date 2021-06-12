<script>
	import Title from '/src/lib/Title.svelte'
	import SearchBar from '/src/components/SearchBar.svelte'
	import NavBarMenus from '/src/lib/NavBar/NavBarMenus.svelte'
	import GenreTab from '/src/lib/Genre/GenreTab.svelte'
	import FavoritesTab from '/src/lib/Favorites/FavoritesTab.svelte';

	export let currentTab;
	let tabItems = [
    	{ label: "Popular", value: "Popular" },
    	{ label: "Top Rated", value: "Top Rated" },
    	{ label: "Upcoming", value: "Upcoming" }
	];
</script>



<nav>
	<Title title="Movie Wiki"/>
	<SearchBar placeholder="Search Movies"/>
	<div class="aside">
		<NavBarMenus bind:activeTabValue={currentTab} items={tabItems} />
		<div class="seperator"></div>
		<GenreTab />
		<FavoritesTab />
	</div>
</nav>


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
</style>