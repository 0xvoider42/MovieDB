<script>
	import { goto } from '$app/navigation';
	import { fly } from 'svelte/transition';

	let inputVal = '';
	let active = false;

	function checkInactive() {
		if (inputVal) {
			active = true;
		} else {
			active = false;
		}
	}

	function submit() {
		goto('/search/' + inputVal);
	}
</script>

<form on:submit|preventDefault={submit} class="search">
	{#if !active}
		<label in:fly={{ y: -10, duration: 200 }} out:fly={{ y: -10, duration: 200 }} for="search"
			>Search for the movie</label
		>
	{/if}
	<input
		on:blur={checkInactive}
		on:focus={() => (active = true)}
		bind:value={inputVal}
		name="search"
		type="text"
		class={active ? 'selected' : ''}
	/>
	{#if inputVal}
		<button in:fly={{ y: 0, duration: 700 }} out:fly={{ y: 0, duration: 700 }}>Search</button>
	{/if}
</form>

<style>
	.search {
		position: relative;
		width: 30%;
		margin: 1rem;
	}
	button {
		font-size: 0.7rem;
		padding: 0rem 1rem;
		background-color: midnightblue;
		color: mintcream;
		font-weight: bold;
		border: none;
		position: absolute;
		bottom: 50%;
		right: 0;
		transform: translate(0, 50%);
		height: 100%;
		border-top-right-radius: 10px;
		border-bottom-right-radius: 10px;
		cursor: pointer;
	}
	input {
		width: 100%;
		font-size: 1rem;
		font-family: Arial, Helvetica, sans-serif;
		font-weight: 600;
		padding: 0.5rem 0.1rem;
		outline: none;
		color: black;
		transition: background 0.75s ease-out;
		background: cadetblue;
		border-radius: 10px;
		padding: 1rem;
	}
	label {
		position: absolute;
		font-size: 0.8rem;
		font-weight: 300;
		top: 50%;
		left: 0;
		transform: translate(0, -50%);
		pointer-events: none;
		color: mintcream;
		padding: 0rem 1rem;
	}
</style>
