<script context="module">
	import { drawRect } from "./_draw.svelte";
	import { right, left, up, down, jump } from "./_keyEvent.svelte";

	export const rendering = () => {
		setInterval(draw, 10);
	};
	// TODO: refact to position
	let x = 0;
	let y = 0;
	export const draw = () => {
		const canvas = document.getElementById(process.env.CANVAS_NAME);
		if (!canvas.getContext) {
			alert("use other browser");
			return;
		}
		const ctx = canvas.getContext("2d");
		ctx.clearRect(0, 0, canvas.width, canvas.height);
		const step = 1;
		if (right === true && x < canvas.width - 42) {
			x += step;
		}
		if (left === true && x > 0) {
			x -= step;
		}
		if (up === true && y > 0) {
			y -= step;
		}
		if (down === true && y < canvas.height - 42) {
			y += step;
		}
		drawRect(ctx, x, y, "red");
	};
</script>
