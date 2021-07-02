<script>
	export let stacks;
</script>

{#each stacks as stack (stack.title)}
<div>
	<h3>{stack.title}</h3>
	<p>Your Rating: {stack.rating}</p>
</div>

{/each}

<style>
	div {
		text-align: left;
		padding-bottom: 10px;
		border-bottom: 1px solid black;
	}

</style>