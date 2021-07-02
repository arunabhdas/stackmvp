<script>
	import StackInput from './StackInput.svelte';
	import StackList from './StackList.svelte';

	export let name;

	let stacks = localStorage.getItem('stacks') ?
							JSON.parse(localStorage.getItem('stacks')) :
							[];

	const submitStack = stack => {
		const updatedStacks = [ ...stacks, stack ];
		localStorage.setItem('stacks', JSON.stringify(updatedStacks))
		stacks = updatedStacks;
	}
</script>

<div class="main">
	<h1>StackMVP - Stacks for your apps</h1>
	<StackInput on:submitStack={event => submitStack(event.detail.stack)}></StackInput>
	<StackList stacks={stacks}/>
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