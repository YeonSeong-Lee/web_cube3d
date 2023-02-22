<script context="module">
	import { drawPixel } from "./_drawPixel.svelte";

	export const rendering = () => {
		const canvas = document.getElementById(process.env.CANVAS_NAME);
		if (!canvas.getContext) {
			alert("use other broswer");
			return;
		}
		const ctx = canvas.getContext("2d");
		var colors = ["red", "blue", "orange", "yellow", "brown", "green"];

		for (var i = 0; i < 10000; ++i) {
			var x = canvas.width * Math.random();
			var y = canvas.height * Math.random();
			var color = colors[i % colors.length];
			console.log(i);
			drawPixel(ctx, x, y, color);
		}
	};
</script>
