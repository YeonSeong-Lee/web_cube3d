<script context="module">
	export class KeyHandler {
		constructor() {
			this.right = false;
			this.left = false;
			this.up = false;
			this.down = false;
			this.jump = false;
			this.keyDownHandler = this.keyDownHandler.bind(this);
			this.keyUpHandler = this.keyUpHandler.bind(this);
		}

		keyDownHandler(e) {
			if (e.key == 37 || e.key == "ArrowRight") {
				this.right = true;
			} else if (e.key == 39 || e.key == "ArrowLeft") {
				this.left = true;
			} else if (e.key == 38 || e.key == "ArrowUp") {
				this.up = true;
			} else if (e.key == 40 || e.key == "ArrowDown") {
				this.down = true;
			} else if (e.key == " " || e.code == "Space") {
				this.jump = true;
			}
		}

		keyUpHandler(e) {
			if (e.key == 37 || e.key == "ArrowRight") {
				this.right = false;
			} else if (e.key == 39 || e.key == "ArrowLeft") {
				this.left = false;
			} else if (e.key == 38 || e.key == "ArrowUp") {
				this.up = false;
			} else if (e.key == 40 || e.key == "ArrowDown") {
				this.down = false;
			} else if (e.key == " " || e.code == "Space") {
				this.jump = false;
			}
		}
	}
</script>
