<script context="module">
	export const getWallColor = (element) => {
		switch (element) {
			case 1:
				return "blue";
			case 2:
				return "green";
			case 3:
				return "black";
			case 4:
				return "yellow";
			default:
				return "white";
		}
	};
</script>
