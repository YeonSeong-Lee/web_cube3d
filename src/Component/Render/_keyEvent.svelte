<script context="module">
	export let right = false;
	export let left = false;
	export let up = false;
	export let down = false;
	export let jump = false;

	export const keyDownHandler = (e) => {
		console.log(e);
		if (e.key == 37 || e.key == "ArrowRight" || e.code == "KeyD") {
			right = true;
		} else if (e.key == 39 || e.key == "ArrowLeft" || e.code == "KeyA") {
			left = true;
		} else if (e.key == 38 || e.key == "ArrowUp" || e.code == "KeyW") {
			up = true;
		} else if (e.key == 40 || e.key == "ArrowDown" || e.code == "KeyS") {
			down = true;
		} else if (e.key == " " || e.code == "Space") {
			jump = true;
		}
	};

	export const keyUpHandler = (e) => {
		if (e.key == 37 || e.key == "ArrowRight" || e.code == "KeyD") {
			right = false;
		} else if (e.key == 39 || e.key == "ArrowLeft" || e.code == "KeyA") {
			left = false;
		} else if (e.key == 38 || e.key == "ArrowUp" || e.code == "KeyW") {
			up = false;
		} else if (e.key == 40 || e.key == "ArrowDown" || e.code == "KeyS") {
			down = false;
		} else if (e.key == " " || e.code == "Space") {
			jump = false;
		}
	};
</script>
