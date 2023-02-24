<script context="module">
	import { drawRect } from "./_draw.svelte";
	import { KeyHandler } from "./_keyEvent.svelte";

	export const rendering = () => {
		setInterval(draw, 1000);
	};

	export const draw = () => {
		const keyHandler = new KeyHandler();
		const canvas = document.getElementById(process.env.CANVAS_NAME);
		if (!canvas.getContext) {
			alert("use other browser");
			return;
		}
		const ctx = canvas.getContext("2d");
		let x = 0;
		let y = 0;
		ctx.clearRect(0, 0, canvas.width, canvas.height);
		const step = 42;
		if (keyHandler.right === true) {
			x += step;
		}
		if (keyHandler.left === true) {
			x -= step;
		}
		if (keyHandler.up === true) {
			y += step;
		}
		if (keyHandler.down === true) {
			y -= step;
		}
		drawRect(ctx, x, y, "red");
		document.addEventListener("keyup", keyHandler.keyUpHandler, false);
		document.addEventListener("keydown", keyHandler.keyDownHandler, false);
	};
</script>
