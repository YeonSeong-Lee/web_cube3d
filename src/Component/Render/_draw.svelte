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
	export const drawPersonalPoint = (
		ctx,
		x,
		y,
		color = "red",
		radius = 10
	) => {
		ctx.beginPath();
		ctx.arc(x, y, radius, 0, 2 * Math.PI);
		ctx.stroke();
		ctx.fillStyle = color;
		ctx.fill();
		ctx.closePath();
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
	export const drawRay = (canvas, map, x, y, dir) => {
		const ctx = canvas.getContext("2d");
		const playerSightRange = 10;
		ctx.beginPath();
		ctx.moveTo(x, y);
		ctx.lineTo(x + dir[0] * playerSightRange, dir[1] * playerSightRange);
		ctx.stroke();
		ctx.closePath();
	};
</script>
