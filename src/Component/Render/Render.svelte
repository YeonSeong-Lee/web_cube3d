<script lang="ts">
	import { beforeUpdate, tick } from 'svelte';
	import { rendering } from "./_rendering.svelte"
	beforeUpdate(async() => {
		await tick();
		rendering();
	})
	const width:number = window.innerWidth * 0.8;
	const height:number = 0.6 * width;
</script>

<div>
	<canvas id=process.env.CANVAS_NAME width = {width} height = {height}></canvas>
</div>

<style>
    canvas {
        border: 1px solid black;
    }
</style>