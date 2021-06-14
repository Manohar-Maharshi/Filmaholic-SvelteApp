<main>
	<h1>See a list of the current popular movies on Internet</h1>
	<div class="border"></div>
<!-- 	<div class="card">
		<div class="stream">
		  		<img src="https://image.tmdb.org/t/p/original/rTh4K5uw9HypmpGslcKd4QfHl93.jpg" class="stream__thumbnail" alt="IMAGE">
		</div>
		<div class="details">
		  	Avengers
		 </div>
	</div> -->
	<div class="card">
		<div class="card-left">
		  	<img src="https://image.tmdb.org/t/p/original/rTh4K5uw9HypmpGslcKd4QfHl93.jpg" alt="IMAGE">
		</div>
		<div class="card-right">
			<h1>Avengers :inifinty war endgae</h1>
			<div class="card-details">
				<ul>
			        <li>2003</li>
			        <li>111 min</li>
			        <li>Action</li>
      			</ul>
      			<div class="overview">
      				Lorem ipsum dolor sit, amet consectetur adipisicing elit. Aliquam animi asperiores in libero voluptatem quam, modi ipsam debitis id dolorum.
      			</div>
      			<button>
      				Read More
      			</button>
			</div>
		</div>	
	</div>

</main>




<style>
	main{
    	z-index: -1 !important;
	}
	h1{
		text-transform: capitalize;
		font-size: 1rem;
    	margin-bottom: 2rem;
	}
		img{
	  	width: 100%;
	}
	.card{
		width: 12rem;
		height: 18rem;
		background-color: gray;
		position: relative;
	}
	.card-left{
		width: 12rem;
	}
	.card-right{
		display: flex;
		flex-direction: column;
		text-align: left;
		position: absolute;
		top: 0;
		left: 12rem;
		width: 0rem;
		height: 18rem;
		background-color: #313131;
		overflow: hidden;
		opacity: 0;
		transition: 0.2s all;
	}
	.card-right h1{
		padding: 0;
		margin: 0;
		margin-top: 0.5rem;
		text-transform: capitalize;
		font-size: 1.5rem;
		color: #772ce8;
	}
	.card-right ul{
		margin: 0.5rem  0;
		display: flex;
		align-items: center;
	}
	.card-right li{
		background-color: gray;
		padding: 0.08rem 0.5rem;
		border-radius: 5px;
		font-size: 0.7rem;
		margin-right: 1rem;
	}
	.overview{
			margin-top: 1rem;
		  display: -webkit-box;
		  -webkit-line-clamp: 4;
		  -webkit-box-orient: vertical;  
		  overflow: hidden;
	}
	.card-right button{
		border: none;
		outline: none;
		background-color: transparent;
		font-family: inherit;
		font-size: 1rem;
		padding: 0.5rem;
		background-color: gray;
		margin-top: 3rem;
		margin-right: 1rem;
		float: right;
	}
	.card:hover .card-right{
		opacity: 1;
		padding: 0.5rem 0.7rem;
		padding-left: 1.5rem;
		width: 25rem;
	}














	.border{
    	margin-bottom: 2rem;
		border: 1px solid #ffffff1a;
	}
	.card{
    	z-index: 1;
	}
	.stream {
	 	position: relative;
	 	display: inline-block;
	 	background-color: #9147ff;
	}
	.details{
		position: absolute;
		display: block;
		top: 0;
		right: 0;
		width: 30rem;
		height: 15rem;
		background-color: lightgray;
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
  	width: 11rem;
	height: 15rem;
    display: block;
    transform: translate(0, 0);
    transition: all .15s ease;
    position: relative;
  }

	.stream:hover .stream__thumbnail {
	  transform: translate(6px, -4px);
	}

	.stream:hover:before {
	  transform: rotate(-45deg) scale(0.9);
	}

	.stream:hover:after {
	  transform: rotate(45deg) scale(0.4);
	}
</style>