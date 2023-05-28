<script>
	import FamilliarTechnology from "./FamilliarTechnology.svelte";
	import { scrollY } from "../../stores.js";
	import "@fontsource/nokora";
	
	let aboutOffset;
	scrollY.subscribe((n) => {
		console.log(n);
		aboutOffset = ((n - 1000) * -0.05) + "%";
	});
</script>

<main>
	<h1 style="--scroll-y: {aboutOffset}"># ABOUT ME</h1>
	<div class="seperator">
		<p class="nokora">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.</p>
		<div class="familliarTechnologies">
			<FamilliarTechnology fileName="svelte" name="Svelte" />
			<FamilliarTechnology fileName="html" name="HTML" />
			<FamilliarTechnology fileName="css" name="CSS" />
			<FamilliarTechnology fileName="javascript" name="JavaScript" />
			<FamilliarTechnology fileName="three.js" name="THREE.JS" />
			<FamilliarTechnology fileName="p5.js" name="p5.js" />
			<FamilliarTechnology fileName="node.js" name="Node.js" />
			<FamilliarTechnology fileName="git" name="git" />
		</div>
	</div>
</main>

<style>
	main {
		background-color: white;
		width: 100vw;
		padding: 0px 0px 10% 0px; 
	}

	.nokora {
		font-family: "Nokora";
	}

	h1 {
		position: relative;
		white-space: nowrap;
		opacity: 0.25;
		font-size: 16em;
		left: var(--scroll-y);
	}

	p {
		font-size: 2.5em;
		margin: 0px 0rem;
		text-indent: 5rem;
		flex-grow: 1;
	}

	.seperator {
		display: flex;
		margin: 6rem 8rem;
		gap: 4rem;
	}

	.familliarTechnologies {
		flex-grow: 1;
		display: grid;
		grid-template-columns: 1fr 1fr 1fr 1fr;
	}
</style>