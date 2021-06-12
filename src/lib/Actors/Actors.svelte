<script>
	import { Accordion, AccordionItem } from "svelte-accessible-accordion";
</script>


<main>
	<div class="container">
			<div class="submenu-header">
			<p class="sub-menu-title">Explore Trending...</p>
			<div on:click={()=> active = false} class="close">
				<svg version="1.1" viewBox="0 0 20 20" x="0px" y="0px" class="ScIconSVG-sc-1bgeryd-1 cMQeyU"><g><path d="M8.5 10L4 5.5 5.5 4 10 8.5 14.5 4 16 5.5 11.5 10l4.5 4.5-1.5 1.5-4.5-4.5L5.5 16 4 14.5 8.5 10z"></path></g></svg>
			</div>

		</div>
<!-- 		<Accordion>
			<AccordionItem expanded title="Title 1">Content 1</AccordionItem>
			<AccordionItem title="Title 2">Content 2</AccordionItem>
	  		<AccordionItem title="Title 3">Content 2</AccordionItem>
		</Accordion> -->
	</div>
</main>




<style>
	main{
		z-index: 999999;
		position: absolute;
		top: 0;
		left: 0;
		transform: translate(0,3rem);
		width: 100%;
		height: 92.25%;
	}
	.container{
		z-index: 99999999;
		margin-top: 0.2rem;
		width: 30rem;
		height: 100%;
				background-color: #18181b;

		box-shadow: 0 1px 10px #00000080,0 10px 8px #00000066;
	}
	.submenu-header{ 
		min-height: 3rem;
	    display: flex;
	    align-items: center;
	    justify-content: space-between;
	    flex-shrink: 0;
	    color: #dedee3;
	    border-top-left-radius: 0.3rem ;
	    border-top-right-radius: 0.3rem ;
	    box-shadow: 0 1px 2px #000000e6,0 0px 2px #000000e6;
	    padding:0 1rem;
	    margin-bottom: 0.2rem;
	}
	.close{
		display: flex;
		align-items: center;
		justify-content: center;
		padding:0.4rem 0;
		border-radius: 0.2rem;
		padding-right: 0.5rem;
		cursor: pointer;
	}
	.close svg{
		margin-left: 0.5rem;
		width: 1rem;
		height: 1rem;
		text-align: center;
		fill: #ffff;
	}
	.close svg{
		width: 1.1rem;
		height: 1.1rem;

	}
	.close:hover{
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