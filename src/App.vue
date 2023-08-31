<script>
import Start from "./pages/start.vue";
import Testing from "./pages/testing.vue";
import Success from "./pages/success.vue";
const routes = {
	"/": Start,
	"/start": Start,
	"/testing": Testing,
	"/success": Success,
};
export default {
	data() {
		return {
			currentPath: window.location.hash,
		};
	},
	computed: {
		currentView() {
			return routes[this.currentPath.slice(1) || "/"] || Start;
		},
	},
	mounted() {
		window.addEventListener("hashchange", () => {
			this.currentPath = window.location.hash;
		});
	},
};
</script>
<template>
	<component :is="currentView" />
</template>
