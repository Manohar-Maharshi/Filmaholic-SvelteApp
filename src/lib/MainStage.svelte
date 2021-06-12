<script>
	import NavBar from './NavBar/NavBar.svelte';
	// import Actors from './Actors/Actors.svelte';

	let selectedTab;

</script>



<main>
	<NavBar bind:currentTab={selectedTab}/>
	<!-- <Actors /> -->
	<!-- {selectedTab} -->
</main>
