<script>
	import StackInput from "./StackInput.svelte";
	export let name;
	export let newProp;

	const submitStack = stack => {
		console.log(stack);
	}
</script>

<div class="main">
	<h1>StackMVP - Stacks for your apps</h1>
	<StackInput on:submitStack={event => submitStack(event.detail.stack)}></StackInput>

</div>
<style>
	.main {

	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

</style>