<script context="module">
	// TODO: refactory for performance,
	// @see https://dirask.com/posts/JavaScript-how-to-draw-pixel-on-canvas-element-n1e7Wp
	export const drawPixel = (ctx, x, y, color) => {
		const roundedX = Math.round(x);
		const roundedY = Math.round(y);
		ctx.fillStyle = color || rgba(0, 0, 0, 0);
		ctx.fillRect(roundedX, roundedY, 1, 1);
	};
</script>
