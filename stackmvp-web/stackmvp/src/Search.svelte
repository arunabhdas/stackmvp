<script>
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	let searchTerm = '';

	const doSearch = event => {
		searchTerm = event.target.value;

		if (searchTerm) {
			dispatch('doSearch', {searchTerm});
		} else {
			dispatch('clearSearch', {});
		}
	}

</script>

<input 
	placeholder="Search your stacks"
	value={searchTerm}
	on:keyup={doSearch}
/>

<style>
	input {
		width: 100%;
	}
</style>