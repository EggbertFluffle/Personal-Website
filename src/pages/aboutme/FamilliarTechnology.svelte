<script>
	import "@fontsource/nokora";
	
	export let fileName;
	export let name;
</script>

<div>
	<img alt={name} src={"./assets/logos/" + fileName + ".jpg"} />
</div>

<style>
	div {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	img {
		width: 50%;
	}
</style>