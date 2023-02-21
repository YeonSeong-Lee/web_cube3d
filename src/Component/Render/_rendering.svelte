<script context="module">
	export const rendering = () => {
		const canvas = document.getElementById(process.env.CANVAS_NAME);
        if (!canvas.getContext)
			return alert('use other broswer');	
		const ctx = canvas.getContext("2d");
	}
</script>