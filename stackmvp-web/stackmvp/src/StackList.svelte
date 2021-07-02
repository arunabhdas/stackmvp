<script>
	export let stacks;
</script>

{#each stacks as stack (stack.title)}
<div>
	<h3>{stack.title}</h3>
	<p>Your Rating: {stack.rating}</p>
</div>

{/each}