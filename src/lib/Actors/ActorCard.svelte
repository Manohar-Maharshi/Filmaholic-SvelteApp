<script>
	export let indexNumber ="";
	export let imgSrc = "";
	export let name = "";
	export let popularityCount ="";
	export let moviesList= "";
</script>



<div class="flip">
	  <div class="front">
			<h1 class="number">{indexNumber}</h1>
	   	<div class="middle">
	   		<img class="image" src="https://image.tmdb.org/t/p/original{imgSrc}" alt="{name}">
	   		<span class="name">{name}</span>
	   	</div>
			<span class="popularity">{popularityCount}</span>		  
		</div>
	  <div class="back">
	    <h2>Popular For :</h2>
	    <p>{moviesList}</p>
	  </div>
</div>



<style>
	.flip {
		overflow: hidden;
		text-align: center;
	  	position: relative;
	  	display: inline-block;
	  	margin-bottom: 1em;
	  	width: 100%;
	  	display: flex;
	  	align-items: center;
	  	justify-content: center;
	}
	.flip img{
		width: 4rem !important;
		height: 4rem !important;
		border-radius: 50% !important;
		object-fit: cover;
		box-shadow: 0px 0px 0px 4px #772ce8;
	}
	.flip > .front,
	.flip > .back {
	  transition-timing-function: cubic-bezier(0.175, 0.885, 0.32, 1.275);
	  transition-duration: 0.4s;
	  transition-property: transform, opacity;
	  height: 100px;
	  padding:1rem 1rem;
	  background: #313131;
	  border-radius: 10px;
	}
	.flip > .back p {
		width: 100%;
		text-align: center;
	  	color: #999;
	}
	.flip > .front {
		display: inline-flex;
		align-items: center;
		justify-content: space-between;
	  	transform: rotateY(0deg);
	}
	.flip > .back {
	  position: absolute;
	  opacity: 0;
	  top: 0px;
	  bottom: 0;
	  left: 0;
	  right: 0;
	  background-color: #313131;
	  width: 100%;
	  transform: rotateY(-180deg);
	}
	.flip:hover > .front {
	  transform: rotateY(180deg);
	}
	.flip:hover > .back {
	  opacity: 1;
	  transform: rotateY(0deg);
	}
	.middle{
		display: flex;
		align-items: center;
		margin-right: 1rem;
	}
	.name{
		width: 220px;
		padding: 1rem 0;
		margin-left: 1rem;
		font-size: 1.3rem;
		color: #772ce8;
		word-wrap: break-word;
	}
	.number{
		font-size: 1.5rem;
		color: gray;
		margin-right: 2rem;
	}
	.popularity{
		margin-left: 0.3rem;
		font-size: 1.4rem;
	  	color: #999;
	}

</style>