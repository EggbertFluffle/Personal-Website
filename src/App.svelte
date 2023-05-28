<script>
	import Landing from "./pages/landing/Landing.svelte";
	import AboutMe from "./pages/aboutme/AboutMe.svelte";
	import { scrollY } from "./stores.js";

	window.addEventListener("scroll", () => {
		scrollY.set(window.scrollY);
	});
</script>

<main>
  <Landing />
	<AboutMe />
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		margin: 0px;
		padding: 0px;
	}
	
	* {
		font-family: sans-seriff;
	}
</style>
