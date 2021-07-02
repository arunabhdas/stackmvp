<script>
	import Search from './Search.svelte';
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

	const clearSearch = () => {
		stacks = localStorage.getItem('stacks') ?
							JSON.parse(localStorage.getItem('stacks')) :
							[];	
	}

	const doSearch = searchTerm => {
		const tempStacks = localStorage.getItem('stacks') ?
							JSON.parse(localStorage.getItem('stacks')) :
							[];	 
		stacks = tempStacks.filter(m => m.title.toLowerCase().includes(searchTerm.toLowerCase()));
	}
</script>

<div class="main">
	<h1>StackMVP - Stacks for your apps</h1>
	<Search on:clearSearch={clearSearch} on:doSearch ={event => doSearch(event.detail.searchTerm)} />
	<StackInput on:submitStack={event => submitStack(event.detail.stack)}></StackInput>
	<StackList stacks={stacks}/>
</div>
<style>
	.main {
		width: 500px;
		max-width: 100%;
		padding: 1em;
		margin: auto;
		text-align: center;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

</style>