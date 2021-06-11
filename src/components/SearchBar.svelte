<script>
	export let value = "";
	export let placeholder ="";

	let activate = true;
	function validate() {
		if(this.value.trim() != ""){
			activate = false;
		}else{
			activate = true;
		}
	}
</script>

<div class="search-bar">
	<input bind:value on:keyup="{validate}" type="search" placeholder="{placeholder}">
	<button class="search-icon {activate ? 'activate' : ''}">
		<svg version="1.1" viewBox="0 0 20 20" x="0px" y="0px" class="ScIconSVG-sc-1bgeryd-1 cMQeyU"><g><path fill-rule="evenodd" d="M13.192 14.606a7 7 0 111.414-1.414l3.101 3.1-1.414 1.415-3.1-3.1zM14 9A5 5 0 114 9a5 5 0 0110 0z" clip-rule="evenodd"></path></g></svg>
	</button>
</div>


<style>
	.search-bar{
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.search-icon{
    	display: flex;
	    -webkit-box-pack: center;
	    justify-content: center;
	    -webkit-box-align: center;
	    align-items: center;
	    padding:0 0.5rem;
	    height: 2.1rem;
	    background-color: #ffffff26;
	    color: #ffffff80;
	    border-top-right-radius: 0.3rem;
    	border-bottom-right-radius: 0.3rem;
    	margin-left: 0.06rem;
    	border: 0;
    	outline: 0;
    	cursor: pointer;
	}
	.search-icon.activate{
		background-color: #ffffff26;
		cursor: not-allowed;
		pointer-events: none;
	}
	.search-icon.activate svg{
		fill: #ffffff80;
		opacity: 0.5;
	}
	.search-icon svg{
		width: 1.4rem;
		height: 1.4rem;
		text-align: center;
		fill: #ffffff;
		opacity: 0.9;
	}
	input[type="search"]{
		font-family: inherit;
		border: none;
		outline: none;
		width: 22rem;
    	height: 2rem;
    	background-color: #ffffff33;
    	border-radius: 0.3rem 0px 0px 0.3rem;
    	padding: 1.05rem 1rem;
    	background-clip: padding-box;
    	line-height: 1.5;
    	font-size: 0.9rem;
    	color: #efeff1;
    	cursor: text;
    	font-weight: 400;
    	transition: box-shadow 100ms ease-in,border 100ms ease-in,background-color 100ms ease-in;
	}
	input[type="search"]:focus{
		background-color: #000;
		box-shadow: 0px 0px 1px 2px rgba(169,112,255,1);
	}
	::placeholder{
    	color: #ffffffb3;
    	text-transform: capitalize;
    	opacity: 0.8;
	}
</style>