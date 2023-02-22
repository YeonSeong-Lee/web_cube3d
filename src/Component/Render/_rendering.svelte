<script context="module">
	export const rendering = () => {
		const canvas = document.getElementById(process.env.CANVAS_NAME);
		if (!canvas?.getContext) {
			alert("use other broswer");
			return;
		}
		const ctx = canvas.getContext("2d");
	};
</script>
