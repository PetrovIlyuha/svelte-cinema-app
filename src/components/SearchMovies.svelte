<script>
	import { goto } from '$app/navigation';
	import { fly } from 'svelte/transition';
	let searchPhrase = '';
	let active = false;
	function cancelInactive() {
		active = searchPhrase.length > 0 ? true : false;
	}
	function submitSearch() {
		goto(`/search/${searchPhrase}`);
		searchPhrase = '';
	}
</script>

<form on:submit|preventDefault={submitSearch} class="search">
	{#if !active}
		<label for="search_input" in:fly={{ y: -20, duration: 400 }} out:fly={{ y: -10, duration: 300 }}
			>Search for movies</label
		>
	{/if}
	<input
		on:focus={() => (active = true)}
		on:blur={cancelInactive}
		on:change={cancelInactive}
		bind:value={searchPhrase}
		type="text"
		name="search_input"
	/>
	{#if searchPhrase}
		<button in:fly={{ x: -10, duration: 400 }} out:fly={{ x: -10, duration: 400 }}>Search</button>
	{/if}
</form>

<style>
	form {
		max-width: 30vw;
		margin-top: 5rem;
		position: relative;
	}
	button {
		font-size: 0.8rem;
		background: rgb(81, 67, 207);
		padding: 0rem 1rem;
		color: white;
		font-weight: 700;
		border: none;
		position: absolute;
		bottom: 50%;
		right: 0;
		transform: translate(50%, 50%);
		height: 100%;
		border-top-right-radius: 10px;
		border-bottom-right-radius: 10px;
	}
	input {
		width: 100%;
		border: none;
		padding: 1rem;
		font-size: 1rem;
		outline: none;
		color: white;
		transition: background 0.8s ease-out;
		font-weight: 700;
		background: rgb(65, 35, 35);
		border-radius: 10px;
	}
	label {
		position: absolute;
		color: rgba(255, 255, 255, 0.637);
		top: 50%;
		transform: translate(0, -60%);
		pointer-events: none;
		padding: 0rem 1rem;
	}
</style>
