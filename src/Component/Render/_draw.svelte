<script context="module">
	import { getWallColor } from "./_getWallColor.svelte";

	// TODO: refactory for performance,
	// @see https://dirask.com/posts/JavaScript-how-to-draw-pixel-on-canvas-element-n1e7Wp
	export const drawPixel = (ctx, x, y, color) => {
		const roundedX = Math.round(x);
		const roundedY = Math.round(y);
		ctx.fillStyle = color || rgba(0, 0, 0, 0);
		ctx.fillRect(roundedX, roundedY, 1, 1);
	};
	export const drawRect = (ctx, x, y, color, width = 42, height = 42) => {
		ctx.fillStyle = color;
		ctx.fillRect(x, y, width, height);
	};
	export const drawMiniMap = (canvas, map) => {
		const ctx = canvas.getContext("2d");
		ctx.fillStyle = "blue";
		for (let i = 0; i < map.length; i++) {
			const row = map[i];
			for (let j = 0; j < row.length; j++) {
				const element = row[j];
				drawRect(
					ctx,
					(j * canvas.width) / row.length,
					(i * canvas.height) / map.length,
					getWallColor(element),
					canvas.width / row.length,
					canvas.height / map.length
				);
			}
		}
	};
</script>
