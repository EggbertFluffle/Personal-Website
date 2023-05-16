<!-- https://www.spinxdigital.com/ -->

<script>
	import FloatingLetters from "./FloatingLetters.svelte";
	import { fade } from 'svelte/transition';
	import { onMount } from 'svelte';

	let mounted = false;

	onMount(() => {
		mounted = true;
	});
</script>

<div class="main">
	<div class="insetBorder">
		<div class="downArrow"></div>
	</div>
	{#if mounted}
		<div class="splashContainer">
			<h1 transition:fade={{ delay: 2000, duration: 1500 }}>My name is Harrison DiAmbrosio,</h1>
			<p transition:fade={{ delay: 2500, duration: 1500 }}>
				a <span>developer</span> devout to making immersive and exspressional web experiences
			</p>
		</div>
	{/if}
	<div class="floatingLettersContainer">
		<FloatingLetters text={"Welcome();"} textSize={128} width={window.innerWidth} height={window.innerHeight} />
	</div>
</div>

<style>
	.main {
		width: 100%;
		height: 100%;
		padding: 0px;
		margin: 0px;
		font-family: "mono";
	}

	.floatingLettersContainer {
		position: absolute;
		top: 0px;
		left: 0px;
		width: 100vw;
		height: 100vh;
		z-index: -1;
	}

	.splashContainer {
		position: absolute;
		font-family: mono-spaced;
		top: 45vh;
		left: 10vw;
	}

	h1 {
		color: white;
		font-size: 4em;
		margin-bottom: 2rem ;
	}

	p {
		color: white;
		font-size: 3em;
		width: 50%;
	}

	.insetBorder {
		display: flex;
		flex-direction: column-reverse;
		position: absolute;
		align-items: center;
		top: 20px;
		left: 20px;
		width: calc(100vw - 40px);
		height: calc(100vh - 40px);
		border: 4px white solid;
		z-index: 1;
	}

	.downArrow {
		width: 20px;
		height: 20px;
		border-left: 4px white solid;
		border-bottom: 4px white solid;
		margin: 2em;
		transform: rotate(-45deg);
	}
</style>