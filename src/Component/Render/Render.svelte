<script>
	import { beforeUpdate, tick } from "svelte";
	import { rendering } from "./_rendering.svelte";
	beforeUpdate(async () => {
		await tick();
		rendering();
	});

	const width = window.innerWidth * 0.7;
	const height = window.innerHeight * 0.7;
</script>

<div>
	<canvas id="process.env.CANVAS_NAME" {width} {height} />
</div>

<style>
	canvas {
		border: 1px solid black;
	}
</style>
