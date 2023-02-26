<script context="module">
	export let right = false;
	export let left = false;
	export let up = false;
	export let down = false;
	export let jump = false;

	export const keyDownHandler = (e) => {
		if (e.key == 37 || e.key == "ArrowRight") {
			right = true;
		} else if (e.key == 39 || e.key == "ArrowLeft") {
			left = true;
		} else if (e.key == 38 || e.key == "ArrowUp") {
			up = true;
		} else if (e.key == 40 || e.key == "ArrowDown") {
			down = true;
		} else if (e.key == " " || e.code == "Space") {
			jump = true;
		}
	};

	export const keyUpHandler = (e) => {
		if (e.key == 37 || e.key == "ArrowRight") {
			right = false;
		} else if (e.key == 39 || e.key == "ArrowLeft") {
			left = false;
		} else if (e.key == 38 || e.key == "ArrowUp") {
			up = false;
		} else if (e.key == 40 || e.key == "ArrowDown") {
			down = false;
		} else if (e.key == " " || e.code == "Space") {
			jump = false;
		}
	};
</script>
