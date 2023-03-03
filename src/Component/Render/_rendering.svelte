<script context="module">
	import {
		drawMiniMap,
		drawPersonalPoint,
		drawRay,
		drawRect,
	} from "./_draw.svelte";
	import {
		right,
		left,
		up,
		down,
		jump,
		rotate_left,
		rotate_right,
	} from "./_keyEvent.svelte";
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
	const dir = [1, 0];

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
		if (rotate_left === true) {
			const radian = Math.PI / 90;
			const tempX =
				Math.cos(-radian) * dir[0] - Math.sin(-radian) * dir[1];
			const tempY =
				Math.sin(-radian) * dir[0] + Math.cos(-radian) * dir[1];
			dir[0] = tempX;
			dir[1] = tempY;
		}
		if (rotate_right === true) {
			const radian = Math.PI / 90;
			const tempX = Math.cos(radian) * dir[0] - Math.sin(radian) * dir[1];
			const tempY = Math.sin(radian) * dir[0] + Math.cos(radian) * dir[1];
			dir[0] = tempX;
			dir[1] = tempY;
		}
		drawMiniMap(canvas, map, x, y);
		drawPersonalPoint(
			ctx,
			x,
			y,
			"red",
			Math.min(canvas.width / map[0].length, canvas.height / map.length) *
				0.42
		);
		drawRay(canvas, map, x, y, dir);
	};
</script>
