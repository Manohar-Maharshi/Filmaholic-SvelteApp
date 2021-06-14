<script>
	import NavBar from './NavBar/NavBar.svelte';
	import Actors from './Actors/Actors.svelte';
	import Popular from '/src/lib/Popular/popular.svelte'

	let selectedTab;

</script>



	<NavBar bind:currentTab={selectedTab}/>
	<Actors />
<main>
	<Popular />
</main>


<style>
	main{
		z-index: -1;
		padding: 0 2rem;
		margin: 2rem auto;
	}
</style>
