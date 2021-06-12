<script>
	import SearchBar from '/src/components/SearchBar.svelte'
	import { Accordion, AccordionItem } from "svelte-accessible-accordion";
	import { fade } from 'svelte/transition';
	import ClickOutside from 'svelte-click-outside';

	let triggerEl;
    let panelVisible = false;


    function togglePanel() {
      panelVisible = !panelVisible;
    }

    function hidePanel() {
      panelVisible = false;
    }
</script>


<section>
	<button bind:this={triggerEl} on:click={togglePanel}  class="pannel-toggle-btn {panelVisible ? 'active' : ''}">
		{#if !panelVisible}
			Trending Actors Across The World &nbsp <svg version="1.1" viewBox="0 0 20 20" x="0px" y="0px" class="ScIconSVG-sc-1bgeryd-1 cMQeyU"><g><path d="M4 16V4H2v12h2zM13 15l-1.5-1.5L14 11H6V9h8l-2.5-2.5L13 5l5 5-5 5z"></path></g></svg>
		{:else}
			<svg version="1.1" viewBox="0 0 20 20" x="0px" y="0px" class="ScIconSVG-sc-1bgeryd-1 cMQeyU"><g><path d="M4 16V4H2v12h2zM13 15l-1.5-1.5L14 11H6V9h8l-2.5-2.5L13 5l5 5-5 5z"></path></g></svg>
		{/if}
	</button>
	<ClickOutside on:clickoutside={hidePanel} exclude={[triggerEl]} class="good">
		<div hidden={!panelVisible} class="container">
			<div class="header">
				<p class="title">Popular Actors</p>
				<SearchBar />
			</div>
			<Accordion>
				<AccordionItem expanded title="Title 1">Content 1</AccordionItem>
				<AccordionItem title="Title 2">Content 2</AccordionItem>
		  		<AccordionItem title="Title 3">Content 2</AccordionItem>
			</Accordion>
		</div>
	</ClickOutside>
</section>

<style>
	section{
		z-index: 999999;
	}
	.container{
		position: absolute;
		top: 0;
		left: 1px;
		transform: translate(0,3.4rem);
		width: 30rem;
		height: 91.5%;
		background-color: #18181b;
		box-shadow: 0 1px 10px #00000080,0 10px 8px #00000066;
		border-bottom: 4px solid #772ce8;
		border-top: 4px solid #772ce8;
	}
	.header{ 
		position: relative;
		height: 6rem;
	    display: flex;
	    align-items: center;
	    justify-content: space-between;
	    flex-direction: column;
	    flex-shrink: 0;
	    color: #dedee3;
	    border-top-left-radius: 0.3rem ;
	    border-top-right-radius: 0.3rem ;
	    /*box-shadow: 0 1px 2px #000000e6,0 0px 2px #000000e6;*/
	    padding:0 1rem;
	    margin-bottom: 0.2rem;
	}
	.title{
		position: relative;
		text-transform: uppercase;
		color: #9147ff;
		font-size: 1.5rem;
		margin-top:0.8rem;
	}
	.pannel-toggle-btn{
		border: 0;
		outline: 0;
		font-family: inherit;
		font-size: inherit;
		display: flex;
		align-items: center;
		justify-content: center;
		position: absolute;
		top: 5rem;
		left: -19rem;
		padding:0.5rem 0.45rem ;
		padding-left: 2rem;
		border-radius: 0.2rem;
		cursor: pointer;
		color: #ffff;
		background-color: rgba(255, 255, 255, 0.3);
		transition: 0.3s left,background-color;
	}
	.pannel-toggle-btn:hover{
		left: -1rem;
		background-color: rgba(255, 255, 255, 0.5);
	}
	.pannel-toggle-btn.active{
		padding:0.5rem 0;
		padding-right: 0.5rem;
		left: 31rem;
		background-color: rgba(255, 255, 255, 0.3);
	}
	.pannel-toggle-btn.active svg{
		margin-left: 0.5rem;
		 transform: rotate(180deg);
	}
	.pannel-toggle-btn svg{
		margin-left: 0.7rem;
		width: 1.5rem;
		height: 1.5rem;
		text-align: center;
		fill: #ffff;
	}
	.pannel-toggle-btn svg{
		width: 1.1rem;
		height: 1.1rem;

	}
	.pannel-toggle-btn:hover{
		background-color: rgba(255, 255, 255, 0.2);
	}
	/*:global([data-accordion]) {
		list-style: none;
		margin-bottom: 1rem;
	}

	:global([data-accordion-item] button) {
		border: 0;
		border-bottom: 1px solid #000;
		font: inherit;
		line-height: inherit;
		color: #000;
		cursor: pointer;
		padding: 0.5rem 1rem;
		width: 100%;
		text-align: left;
		margin: 0;
	}

	:global([data-accordion-item] [role="region"]) {
		padding: 2rem;
	}*/
</style>