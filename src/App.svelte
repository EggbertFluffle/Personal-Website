<script>
	import Landing from "./pages/landing/Landing.svelte";
</script>

<main>
  <Landing />
</main>

<style>
  h1 {
		font-family: mono;
		text-align: center;
		font-size: 10em;
		background-image: linear-gradient(90deg, purple, purple, black);
		background-clip: text;

		-webkit-background-clip: text;
	  -webkit-text-fill-color: transparent; 
	  -moz-background-clip: text;
	  -moz-text-fill-color: transparent;

		animation: 10s infinite;
	}

	@keyframes gradient_rotate {
		from {
			background-image: linear-gradient(0deg, purple, #af4261);
		}

		to {
			background-image: linear-gradient(180deg, purple, #af4261);
		}
	}
</style>
