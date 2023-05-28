ff<!-- https://www.spinxdigital.com/ -->

<script>
	import FloatingLetters from "./FloatingLetters.svelte";
	import { fade } from 'svelte/transition';
	import { onMount } from 'svelte';
	import "@fontsource/zcool-kuaile"
	import "@fontsource/nokora";

	let mounted = false;

	onMount(() => {
		mounted = true;
	});
</script>

<main>
	<svg width="" height="">
    <polygon points={`${window.innerWidth * 0.85},0 0,${window.innerHeight} ${window.innerWidth},${window.innerHeight}`}/>
  </svg>
	{#if mounted}
		<div class="splashContainer">
			<h1 class="nokora" transition:fade={{ delay: 2000, duration: 1500 }}>My name is <span class="name">Harrison DiAmbrosio</span>,</h1>
			<p class="nokora" transition:fade={{ delay: 2500, duration: 1500 }}>
				a developer devout to making immersive and exspressional web experiences
			</p>
		</div>
	{/if}
	<div class="floatingLettersContainer">
		<FloatingLetters text={"Welcome();"} textSize={164} width={window.innerWidth} height={window.innerHeight} />
	</div>
</main>

<style>
	main {
		width: 100vw;
		height: 100vh;
		padding: 0px;
		margin: 0px;
	}

	.nokora {
		font-family: nokora;
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
		font-size: 5em;
		margin-bottom: 2rem ;
	}

	p {
		color: white;
		font-size: 3em;
		width: 50%;
		font-weight: 100;
	}

	svg {
		position: absolute;
		fill: white;
		mix-blend-mode: difference;
		z-index: 2;
	}

	.name {
		font-family: "ZCOOL KuaiLe", sans-seriff;
	}
</style>