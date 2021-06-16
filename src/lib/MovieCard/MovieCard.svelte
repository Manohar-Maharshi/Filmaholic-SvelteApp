<script>
	import ClickOutside from 'svelte-click-outside';
	import Button from '/src/components/GoogyButton.svelte';
	import Loader from '/src/components/Loader.svelte';


		export let loadURL;


		let movieList =[];
		let specificMovieData = [];
		let movieCast;
		let movieTrilerLink;
	  let panelVisible = false;


    function togglePanel() {
      panelVisible = !panelVisible;
    }

    function hidePanel() {
      panelVisible = false;
    }

    const convertMinsToHrsMins = (mins) => {
		  let h = Math.floor(mins / 60);
		  let m = mins % 60;
		  m = m < 10 ? '0' + m : m;
		  return `${h} Hours ${m} Minutes`;
		}


   	async function renderData(id){
	    		movieCast = "";
	    		specificMovieData= [];
	    		movieTrilerLink = "";
	    		const resp = await fetch(`https://api.themoviedb.org/3/movie/${id}?api_key=04c35731a5ee918f014970082a0088b1&language=en-US`);
	    		const resp2 = await fetch(`https://api.themoviedb.org/3/movie/${id}/credits?api_key=04c35731a5ee918f014970082a0088b1&language=en-US`);
	    		const resp3 = await fetch(`https://api.themoviedb.org/3/movie/${id}/videos?api_key=04c35731a5ee918f014970082a0088b1&language=en-US`)
	    		const js = await resp.json();
	    		const js2 =  await resp2.json();
	    		const js3 = await resp3.json();
	    		specificMovieData.push(js);
	    		specificMovieData = specificMovieData;
	    		movieCast = js2.cast;
	    		movieCast = movieCast;
	    		movieTrilerLink = js3.results[0].key;
    }

	let promise = Promise.resolve([]);
    async function getMovieThumbData(){
    	const response1 = await fetch(`${loadURL}`);
    	const json1 = await response1.json();
    	movieList = []
    	json1.results.forEach((result)=>{
    		async function getData(){
	    		const response2 = await fetch(`https://api.themoviedb.org/3/movie/${result.id}?api_key=04c35731a5ee918f014970082a0088b1&language=en-US`);
	    		const json2 = await response2.json();
	    		movieList.push(json2);
	    		movieList = movieList;
    		}
    	getData()
    	})
    }
   	getMovieThumbData();
</script>

<section class="cards-warapper">
		{#each movieList as {id,backdrop_path,vote_average,title,release_date,original_language,genres}}
			<div class="card">
				<div class="stream">
				  	<img loading="lazy" src="https://image.tmdb.org/t/p/original{backdrop_path}" class="stream__thumbnail" alt="IMAGE">
						<div class="image-stats">
							<p class="movies-rating">
								{vote_average} Rating
							</p>
						</div>
				</div>
				<div class="bio">
					<p on:click={togglePanel} on:click={renderData(id)} class="movie-name" title="{title}">
						{title}
					</p>
					<div class="movie-stats">
							<p class="release-date">{release_date}</p>
							<span>&middot;</span>
							<p class="language">{original_language}</p>
					</div>
					<div class="genre-pills">
						{#each genres as {name}}
							<p class="genre-pill">{name}</p>
						{/each}
					</div>
				</div>
			</div>
		{:else}
			<Loader />
	{/each}
</section>



{#each specificMovieData as item}
	<div hidden={!panelVisible} class="movie-details-overlay" >
		<div class="header">
			<button class="btn-close" on:click={togglePanel} data-tooltip="Close" data-tooltip-location="left">
				<svg version="1.1" viewBox="0 0 20 20" x="0px" y="0px" ><g><path d="M8.5 10L4 5.5 5.5 4 10 8.5 14.5 4 16 5.5 11.5 10l4.5 4.5-1.5 1.5-4.5-4.5L5.5 16 4 14.5 8.5 10z"></path></g></svg>			
			</button>
		</div>
		<div class="main-content">
			<div class="content-left">
				<img class="cover-img" loading="eager" src="https://image.tmdb.org/t/p/original{item.poster_path}" alt="{item.title}">
				<div class="cast">
					<ul>
						{#each movieCast as cast}
						<li>
							<div class="member">
								<img loading="eager" src="https://image.tmdb.org/t/p/original{cast.profile_path}" alt="{cast.name}">
								<p class="original-name">{cast.name}</p>
								<p class="acting-name">({cast.character})</p>
							</div>
						</li>
						{/each}
					</ul>
				</div>
			</div>
			<div class="content-right">
				<h2 class="mv-title">{item.title}</h2>
				<div class="meta-data">
					<p>Tagline: <span>{item.tagline}</span></p>
					<p>Release Date: <span>{item.release_date}</span></p>
					<p>Genres: {#each item.genres as {name}}<span>{name + "  "}</span>{/each}</p>
					<p>Runtime: <span>{convertMinsToHrsMins(item.runtime)}</span></p>
					<p>Language: <span>{item.original_language.toUpperCase()}</span></p>
					<p>Budget: <span>{item.budget.toString().replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ",")}</span></p>
					<p>Revenue: <span>{item.revenue.toString().replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ",")}</span></p>
					<p>Production Companies: {#each item.production_companies as {name,origin_country}}<span>{ name+ `(${origin_country})` + "  "}</span>{/each}</p>
				</div>
				<div class="border"></div>
				<div class="overview">
					<h2>Storyline:</h2>
					<p>{item.overview}</p>
			    <div class="trailer">
			    	<Button name="Watch Trailer" url="https://www.youtube.com/watch?v={movieTrilerLink}"/>
			    </div>
				</div>
			</div>
		</div>		
	</div>
{/each}



<style>
.cards-warapper{
		margin: 0 2rem;
		display: flex;
		align-items: center;
		flex-wrap: wrap;
		justify-content: space-between;
}
	.movie-details-overlay{
		z-index: 9999999;
		position: absolute;
		top: 0;
		right: 0px;
		transform: translate(1rem,3.4rem);
		right: 1rem;
		width: 50rem;
		height: 91.5%;
		border-radius: 0.3rem;
		background-color: #18181b;
		box-shadow: 0 1px 10px #00000080,0 10px 8px #00000066;
		border-bottom: 4px solid #772ce8;
		border-top: 4px solid #772ce8;
	}
	.btn-close{
		margin: 1rem;
		border: none;
		outline: none;
		float: right;
		justify-content: center;
		padding:0.2rem 0.4rem;
		padding-top: 0.4rem;
		border-radius: 0.2rem;
		cursor: pointer;
		background-color: rgba(255, 255, 255, 0.2);
		color: #fff !important;
		background-color: #772ce8;
	}
	.btn-close svg{
		width: 1.1rem;
		height: 1.1rem;
		fill: #fff;
		padding: 0;
		margin: 0;
	}
	.btn-close:hover{
		background-color: rgba(255, 255, 255, 0.2);
	}
	.content-left{
		display: flex;
		align-items: center;
		justify-content: flex-start;
		flex-direction: column;
	}
	.content-right{
		margin-left: 1rem;

	}
	.cast{
		margin-top: 0.7rem;
		text-align: center;
		width: 100%;
		height: 19rem;
		overflow: hidden;
	}
	.cast:hover{
		overflow-y: overlay;
	}
	.cast li{
		margin: 0.5rem 0;
		margin-bottom: 0.8rem;
	}
	.member img{
		width: 3rem;
		height: 3rem;
		border-radius: 50px;
		object-fit: cover;
		box-shadow: 0px 0px 0px 4px #772ce8;
	}
	.member p{
		display: flex;
		align-items: center;
		flex-direction: column;
		text-align: center;
		font-size: 0.8rem;
		text-overflow: ellipsis;
    	white-space: wrap;
    	word-break: break-word;
    	overflow: hidden;
	}
	.member .as{
		font-size: 0.5rem;
		margin: 0;
		padding: 0;
	}
	.member .acting-name{
		color: #772ce8;
	}








	.main-content{
		margin-top: 1.2rem;
		margin-left: 1.3rem;
		display: flex;
	}
	.cover-img{
		margin-top: 1rem;
		margin-right: 0.2rem;
		width: 10rem;
		height:auto;
		border-radius: 1px;
		object-fit: contain;
		box-shadow: 0px 0px 0px 2px rgba(119,44,232,1);
	}
	.mv-title{
		font-size: 1.5rem;
	}
	.meta-data{
		margin-top: 0.2rem;
		line-height: 1.7rem;
	}
	.meta-data p{
		font-weight: 600;
		color: #772ce8;
	}
	.meta-data p span{
		font-weight: normal;
		margin-left: 0.2rem;
		color: #ffffff;
	}
	.border{
		margin: 0.5rem 0;
    	border: 1px solid #ffffff1a;
	}
	.overview h2{
		color: #772ce8;
		font-size: 1.1rem;
	}
	.overview p{
		display: -webkit-box;
		-webkit-line-clamp: 5;
		-webkit-box-orient: vertical;  
		overflow: hidden;
	}
	.watch-triler{
		border: 1px solid #FF0000;
		margin-top: 2rem;
	}
.overview .trailer{
	display: flex;
	align-items: center;
	justify-content: center;
	margin-top: 3rem;
}


















	.card{
    	z-index: 1;
		width: 19.1rem;
		outline: 2px solid transparent;
		margin: 0.5rem;
		margin-bottom: 0.8rem;
	}
	.movies-rating{
		position: absolute;
		top: 0;
		left: 0;
		margin: 0.6rem;
		padding: 0px 0.3rem;
	    display: flex;
	    align-items: center;
	    justify-content: center;
	    background-color: #e91916;
	    color: #fff;
	    font-size: 0.7rem;
	    border-radius: 0.1rem;
	    text-align: center;
	    text-transform: uppercase;
	  	transition: all .15s ease;
	}
	.bio{
		color: #dedee3;
		width: 19.1rem;
		padding: 0 0.2rem;
	}
	.movie-name{
    font-size: 1rem;
		text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
		cursor: pointer;
	}
	.movie-name:hover{
		color: #a970ff;
	}
	.movie-stats{
		margin: 0.2rem 0.1rem;
		text-transform: uppercase;
		display: flex;
		align-items: center;
		font-size: 0.75rem;
	}
	.movie-stats span{
		margin: 0 0.4rem;
	}
	.genre-pills{
		margin: 0.2rem 0;
	}
	.genre-pill{
		cursor: default;
		display: inline-flex;
		align-items: center;
	    border-radius: 9000px;
	    font-weight:600;
	    color: #ffffffb3;
	    background-color: #ffffff26;
	    text-align: center;
	    font-size: 0.6rem;
	    padding: 0px 0.4rem;
	    border: 2px solid transparent;
	    vertical-align: middle;
	    margin-right: 0.3rem;
	}
	.stream {
	 	position: relative;
	 	display: inline-block;
	 	background-color: #9147ff;
	}
	.stream:hover ~ .details{
		display: block;
	}
	  .stream:before,
	  .stream:after {
	    content: '';
	    display: block;
	    background-color: #9147ff;
	    width: 8px;
	    height: 8px;
	    position: absolute;
	    transition: all .15s ease;
	  }

  .stream:before {
    top: 0;
    left: 0;
    transform-origin: top left;
    transform: rotate(-45deg) scale(0);
  }

  .stream:after {
    right: 0;
    bottom: 0;
    transform-origin: bottom right;
    transform: rotate(45deg) scale(0);
  }

  .stream__thumbnail {
  	z-index: 0;
  	width: 19.1rem;
  	height: auto;
    display: block;
    transform: translate(0, 0);
    transition: all .15s ease;
    position: relative;
  }

	.stream:hover .stream__thumbnail,
	.stream:hover	.movies-rating {
	  transform: translate(6px, -4px);
	}

	.stream:hover:before {
	  transform: rotate(-45deg) scale(0.9);
	}

	.stream:hover:after {
	  transform: rotate(45deg) scale(0.4);
	}
</style>