<script context="module">
	import { drawMiniMap, drawPersonalPoint, drawRect } from "./_draw.svelte";
	import { right, left, up, down, jump } from "./_keyEvent.svelte";
	import { map } from "../../map.svelte";
	import {
		isPossibleToRight,
		isPossibleToLeft,
		isPossibleToUp,
		isPossibleToDown,
	} from "./_wallCollision.svelte";

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
		if (right === true && isPossibleToRight(canvas, x, y, step)) {
			x += step;
		}
		if (left === true && isPossibleToLeft(canvas, x, y, step)) {
			x -= step;
		}
		if (up === true && isPossibleToUp(canvas, x, y, step)) {
			y -= step;
		}
		if (down === true && isPossibleToDown(canvas, x, y, step)) {
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
