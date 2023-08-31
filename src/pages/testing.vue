<script>
export default {
	mounted() {
		this.startPainting();
	},
	methods: {
		startPainting() {
			var canvas = this.$refs.MainCanvas;
			var CanvasContext = canvas.getContext("2d");
			canvas.height = window.innerHeight;
			canvas.width = window.innerWidth;
			var chars = "XIAOUN01";
			chars = chars.split("");
			var fontSize = 16;
			var columns = Math.floor(canvas.width / fontSize);
			var drops = new Array(columns);
			// drops = drops.fill(1, 0, columns - 1);
			for (var x = 0; x < columns; x++) drops[x] = (-Math.random() / 3) * canvas.height;

			var processBlocks = 0;
			var processBarY = Math.round((0.75 * canvas.height) / fontSize);

			function draw() {
				CanvasContext.fillStyle = "rgba(48, 48, 48, 0.1)";
				CanvasContext.fillRect(0, 0, canvas.width, canvas.height);
				CanvasContext.fillStyle = "#FF4181";
				CanvasContext.font = fontSize + "px Roboto";
				for (var i = 0; i < drops.length; i++) {
					var text = chars[Math.floor(Math.random() * chars.length)];
					CanvasContext.fillText(text, i * fontSize, drops[i] * fontSize);
					if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
					drops[i]++;
				}

				//绘制进度条
				CanvasContext.fillText(" [", fontSize, processBarY * fontSize);
				for (var i = 0; i + 20 < processBlocks; i++) {
					CanvasContext.fillText("█", (i + 2) * fontSize, processBarY * fontSize);
				}
				CanvasContext.fillText("]", (columns - 2) * fontSize, processBarY * fontSize);
				processBlocks++;
				if (processBlocks - 20 > columns - 4) {
					clearInterval(timer);
					window.location.replace("#/success");
				}
			}
			var timer = setInterval(draw, 50);
		},
	},
};
</script>
<template>
	<canvas ref="MainCanvas" id="ad"></canvas>
</template>

<style scope>


canvas {
	display: block;
}
</style>
