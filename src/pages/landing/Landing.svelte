<script>
	import FloatingLetters from "./FloatingLetters.svelte";
	import { onMount } from 'svelte';

	let container;
</script>

<main bind:this={container}>
	<FloatingLetters text="Hola" width={window.innerWidth} height={window.innerHeight} />
</main>

<style>
	main {
		width: 100%;
		height: 100%;

		background-color: red;
		padding: 0px;
		margin: 0px;
	}
</style>