<template>
	<v-app>
		<v-app-bar title="GalievDev">
			<v-spacer></v-spacer>

			<v-btn
				href="https://github.com/GalievDev"
				prepend-icon="mdi-github"
				target="blank"
				>GitHub</v-btn
			>
		</v-app-bar>
		<Home />
	</v-app>
</template>

<script lang="ts">
import Home from './components/Home.vue'

export default {
	components: {
		Home,
	},
}
</script>
