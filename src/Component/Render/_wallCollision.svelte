<script context="module">
	import { map } from "../../map.svelte";

	export const isPossibleToRight = (canvas, x, y, step) => {
		return (
			x < canvas.width - canvas.width / map[0].length &&
			map[Math.round((y / canvas.height) * map.length)][
				Math.round(((x + step) / canvas.width) * map[0].length)
			] === 0
		);
	};

	export const isPossibleToLeft = (canvas, x, y, step) => {
		return (
			x > 0 &&
			map[Math.round((y / canvas.height) * map.length)][
				Math.round(((x - step) / canvas.width) * map[0].length) - 1
			] === 0
		);
	};

	export const isPossibleToUp = (canvas, x, y, step) => {
		return (
			y > 0 &&
			map[Math.round(((y - step) / canvas.height) * map.length) - 1][
				Math.round((x / canvas.width) * map[0].length)
			] === 0
		);
	};

	export const isPossibleToDown = (canvas, x, y, step) => {
		return (
			y < canvas.height - canvas.height / map.length &&
			map[Math.round(((y + step) / canvas.height) * map.length)][
				Math.round((x / canvas.width) * map[0].length)
			] === 0
		);
	};
</script>
