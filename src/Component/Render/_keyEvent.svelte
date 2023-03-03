<script context="module">
	export let right = false;
	export let left = false;
	export let up = false;
	export let down = false;
	export let jump = false;
	export let rotate_left = false;
	export let rotate_right = false;

	export const keyDownHandler = (e) => {
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
		} else if (e.key == "q" || e.code == "KeyQ") {
			rotate_left = true;
		} else if (e.key == "e" || e.code == "KeyE") {
			rotate_right = true;
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
		} else if (e.key == "q" || e.code == "KeyQ") {
			rotate_left = false;
		} else if (e.key == "e" || e.code == "KeyE") {
			rotate_right = false;
		}
	};
	document.addEventListener("keyup", keyUpHandler, false);
	document.addEventListener("keydown", keyDownHandler, false);
</script>
