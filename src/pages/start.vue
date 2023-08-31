<script>
import mdui from "mdui";
export default {
	methods: {
		startTesting() {
			window.location.replace("#/testing");
		},
		quickTest() {
			mdui.alert("恭喜您！您的设备能够正常开机！", "检测通过");
		},
	},
};
</script>

<template>
	<div id="main-container" class="mdui-container mdui-valign mdui-theme-primary-indigo mdui-theme-accent-pink">
		<div id="start-test-card" class="mdui-center mdui-card mdui-row-12 mdui-col-sm-6 mdui-col-md-4">
			<div class="mdui-card-media">
				<img src="../medias/dato-logo.webp" />

				<!-- 卡片的标题和副标题 -->
				<div class="mdui-card-primary">
					<div class="mdui-card-primary-title">测试你的设备是否能够正常开机</div>
					<div class="mdui-card-primary-subtitle">Device Available Test Online</div>
				</div>
			</div>

			<!-- 卡片的按钮 -->
			<div class="mdui-card-actions">
				<button class="mdui-btn mdui-ripple mdui-color-theme-accent" @click="startTesting">开始测试</button>
				<button class="mdui-btn mdui-ripple mdui-color-theme-accent" @click="quickTest">快速测试</button>
			</div>

			<!-- <div class="mdui-card-content">
				<blockquote>
					<p>
						当我年轻时，我画得像个孩子，但我画画的时候，我想象着成为大师的一天。
						尽管我现在的作品还不完美，但我相信每一次努力都是迈向卓越的一步。
						每一个伟大的成就都开始于那些看似平凡的努力和坚持。 艺术是一个不断进化的过程，今天的粗糙将成为明天的精湛。
						不要害怕失败，因为失败是成功的垫脚石，只要你保持努力和学习，你一定会取得成就。
					</p>
					<footer>——ChatGPT</footer>
				</blockquote>
			</div> -->
		</div>
	</div>
</template>

<style>
#main-container {
	height: 100vh;
}
</style>
