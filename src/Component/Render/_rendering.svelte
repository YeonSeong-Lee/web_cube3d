<script context="module">
	import { drawMiniMap, drawPersonalPoint, drawRect } from "./_draw.svelte";
	import { right, left, up, down, jump } from "./_keyEvent.svelte";
	import { map } from "../../map.svelte";
	import { intros } from "svelte/internal";

	export const rendering = () => {
		setInterval(draw, 10);
	};
	// TODO: refact to position
	let x = 42;
	let y = 42;

	const draw = () => {
		const canvas = document.getElementById(process.env.CANVAS_NAME);
		if (!canvas.getContext) {
			alert("use other browser");
			return;
		}
		const ctx = canvas.getContext("2d");
		ctx.clearRect(0, 0, canvas.width, canvas.height);
		const step = 1;
		if (
			right === true &&
			x < canvas.width - canvas.width / map[0].length &&
			map[Math.round((y / canvas.height) * map.length)][
				Math.round(((x + step) / canvas.width) * map[0].length)
			] === 0
		) {
			x += step;
		}
		if (
			left === true &&
			x > 0 &&
			map[Math.round((y / canvas.height) * map.length)][
				Math.round(((x - step) / canvas.width) * map[0].length)
			] === 0
		) {
			x -= step;
		}
		if (
			up === true &&
			y > 0 &&
			map[Math.round(((y - step) / canvas.height) * map.length)][
				Math.round((x / canvas.width) * map[0].length)
			] === 0
		) {
			y -= step;
		}
		if (
			down === true &&
			y < canvas.height - canvas.height / map.length &&
			map[Math.round(((y + step) / canvas.height) * map.length)][
				Math.round((x / canvas.width) * map[0].length)
			] === 0
		) {
			y += step;
		}
		drawMiniMap(canvas, map);
		drawPersonalPoint(
			ctx,
			x,
			y,
			"red",
			Math.min(canvas.width / map[0].length, canvas.height / map.length) *
				0.8
		);
	};
</script>
