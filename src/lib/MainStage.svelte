<script>
	import NavBar from './NavBar/NavBar.svelte';
	import Actors from './Actors/Actors.svelte';
	import MovieCard from '/src/lib/MovieCard/MovieCard.svelte'

	let selectedTab;
	let inputVal;
	let value;
	
	$: value = inputVal

	let PopularMoviesUrl = "https://api.themoviedb.org/3/movie/popular?api_key=04c35731a5ee918f014970082a0088b1&language=en-US&page=1"
	let TopMoviesUrl = "https://api.themoviedb.org/3/movie/top_rated?api_key=04c35731a5ee918f014970082a0088b1&language=en-US&page=1"
	let NowPlayingMoviesUrl = "https://api.themoviedb.org/3/movie/now_playing?api_key=04c35731a5ee918f014970082a0088b1&language=en-US&page=1"
	let UpcomingMoviesUrl = "https://api.themoviedb.org/3/movie/upcoming?api_key=04c35731a5ee918f014970082a0088b1&language=en-US&page=1"

	
</script>
	


	<NavBar bind:inputValue={inputVal} bind:currentTab={selectedTab}/>
	<Actors />
<main>
	{#if value}
		<h1>
			you searched for <span class="link">"{value}"</span>
		</h1>
		<div class="border"></div>
		<MovieCard loadURL={`https://api.themoviedb.org/3/search/movie?api_key=04c35731a5ee918f014970082a0088b1&language=en-US&query=${value}&page=1&include_adult=true`} />	
		<div class="border"></div>
	{/if}
		{value = ""}
		{#if selectedTab === "Popular"}
			<h1>
				<span class="link">{selectedTab}</span> movies on Internet
			</h1>
			<div class="border"></div>
			<MovieCard loadURL={PopularMoviesUrl}/>
		{:else if selectedTab === "Top Rated"}
			<h1>
				<span class="link">{selectedTab}</span> movies on Internet
			</h1>
			<div class="border"></div>
			<MovieCard loadURL={TopMoviesUrl} />
		{:else if selectedTab === "Now Playing"}
			<h1>
				 movies <span class="link">{selectedTab}</span> on theatres
			</h1>
			<div class="border"></div>
			<MovieCard loadURL={NowPlayingMoviesUrl} />
		{:else}
			<h1>
				<span class="link">{selectedTab}</span> movies on Internet
			</h1>
			<div class="border"></div>
			<MovieCard loadURL={NowPlayingMoviesUrl} />
		{/if}

</main>


<style>
	main{
		z-index: -1;
		padding: 0 0rem;
		margin: 2rem auto;
		margin-top: 1.7rem;
	}
	h1{
		text-transform: capitalize;
		font-size: 1.6rem;
    	margin-bottom: 1.7rem;
    	text-align: center;
   		vertical-align: top;

	}
	.border{
    	margin-bottom: 2rem;
		border: 1px solid #ffffff1a;
	}
.link {
	text-align: center;
   padding: 3px 0.7rem;
   overflow: hidden;
   color: #fff;
   transition: color .3s ease-out;
   background: linear-gradient(90deg, rgba(119,44,232,1) 0%, rgba(100,32,203,1) 100%);
   border-radius: 1px;
}

</style>
