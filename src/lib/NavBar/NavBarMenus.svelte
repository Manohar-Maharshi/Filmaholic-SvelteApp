<script>
	  import { onMount } from "svelte";

	  export let items = [];
	  export let activeTabValue;

	  onMount(() => {
	    if (Array.isArray(items) && items.length && items[0].value) {
	      activeTabValue = items[0].value;
	    }
	  });

	  const handleClick = tabValue => () => (activeTabValue = tabValue);
</script>

<ul>
  {#if Array.isArray(items)}
    {#each items as item}
      <li class={activeTabValue === item.value ? 'active' : ''}>
        <a href="#" on:click={handleClick(item.value)}>{item.label}</a>
      </li>
    {/each}
  {/if}
</ul>

<style>
  	ul{
		display: flex;
		user-select: none;
	}
	li {
		margin-right: 1rem;
	}
	li:last-child{
		margin-right: 0;
	}
	li a{
		text-transform: capitalize;
		text-align: center;
		padding:0.8rem 0.5rem;
		transition: .01s all;
		cursor: pointer;
		font-size: 0.9rem;
	}
	li.active > a{
		color: #a970ff;
		border-bottom: 2px solid #772ce8;
	}
	li a:hover{
		color: #a970ff;
	}
</style>