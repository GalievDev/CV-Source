<template>
	<v-main>
		<!-- About -->
		<v-container class="text-center mt-16 w-50">
			<v-divider></v-divider>
			<v-avatar rounded="4" :size="size" class="mt-16">
				<v-img src="https://i.ibb.co/VTw5bLP/galiev.jpg" alt="galiev"></v-img>
			</v-avatar>
			<v-container class="text-center mt-16" :size="size">
				<p class="text-h3" style="font-weight: 500">Hi! My name is Vazir.</p>
				<p class="text-h5 mt-6 mb-16" style="font-weight: 300">
					I am 17 years old. I'm a Java developer from Tashkent for more than 2
					years. My main areas are web development, modding in FabricMC and
					creating desktop applications in JavaFX. I like to solve all kinds of
					new tasks for me and I approach them very responsibly.
				</p>
			</v-container>
			<v-divider></v-divider>
		</v-container>
		<!-- End About -->

		<!-- Education -->
		<v-container
			class="justify-center text-center w-auto mb-16 overflow-visible"
		>
			<v-container class="w-50">
				<p class="text-h3" style="font-weight: 500">Educations</p>
				<v-card class="text-center mt-16 mb-16" variant="outlined">
					<v-card-title><b class="text-h5">Hight School №2</b> </v-card-title>
					<p style="color: grey">Sep 2012 - Jun 2023</p>
					<v-card-text class="text-h6" style="font-weight: 300">
						<p>
							In 9th grade I already started learning programming and creating
							my first Minecraft mod. I solved problems in physics and
							mathematics, as well as studying history. In 11th grade I decided
							to devote myself entirely to Java development.
						</p>
					</v-card-text>
				</v-card>
				<v-card
					class="text-center overflow-x-auto mt-16 mb-16"
					variant="outlined"
				>
					<v-card-title><b class="text-h5">BePro IT Academy</b> </v-card-title>
					<p style="color: grey">Oct 2022 - Feb 2023</p>
					<v-card-text class="text-h6" style="font-weight: 300">
						<p>
							In these courses I finally learned the core of Java. I learned how
							to create web applications on Spring framework and desktop
							applications on JavaFX. At the end of the course I received a
							certificate certifying that I have learned the basics of Java
							programming.
						</p>
					</v-card-text>
				</v-card>
				<v-divider></v-divider>
			</v-container>
		</v-container>
		<!-- End Education -->

		<!-- Projects -->
		<v-container class="text-center w-auto mb-16">
			<v-container class="w-75">
				<p class="text-h3" style="font-weight: 500">My Projects</p>
				<p class="text-h4 mt-16" style="font-weight: 300">Minecraft</p>
				<v-container>
					<v-row class="justify-center">
						<v-col
							xs="1"
							sm="1"
							md="2"
							lg="3"
							xl="3"
							v-for="project in projects"
							:key="project.id"
						>
							<v-card
								variant="outlined"
								height="auto"
								width="auto"
								class="mt-6 justify-center"
							>
								<v-avatar class="mt-5" :image="project.icon_url"></v-avatar>
								<v-card-title class="text-h6">{{ project.title }}</v-card-title>
								<v-card-text style="color: grey">
									{{ project.description }}</v-card-text
								>
								<p>Downloads: {{ project.downloads }}</p>

								<v-container class="justify-center">
									<v-btn
										class="mt-5"
										prepend-icon="mdi-download"
										:href="'https://modrinth.com/mod/' + project.slug"
										target="blank"
										>Download</v-btn
									>
									<v-btn
										class="mt-5 ml-5 mr-5"
										prepend-icon="mdi-github"
										:href="'https://modrinth.com/mod/' + project.source_code"
										target="blank"
										>Source</v-btn
									>
								</v-container>
							</v-card>
						</v-col>
					</v-row>
				</v-container>
				<p class="text-h4 mt-16 mb-5" style="font-weight: 300">
					Other Projects
				</p>
				<v-container class="justify-center">
					<v-btn
						prepend-icon="mdi-github"
						target="blank"
						href="https://github.com/GalievDev?tab=repositories"
						>You can see them on my GitHub</v-btn
					>
				</v-container>
			</v-container>
		</v-container>
		<!-- End Projects -->

		<!-- Contacts -->
		<v-container class="text-center w-auto mb-16 justify-center">
			<v-container class="w-50">
				<v-divider></v-divider>
				<v-card class="mt-16 mb-16" variant="outlined">
					<v-card-title class="text-h3 mt-16">Contacts</v-card-title>
					<v-card-text class="text-h6 mt-6"
						>If you want to contact me:</v-card-text
					>
					<v-container class="mb-16 justify-center">
						<v-btn
							class="mr-6 mb-6"
							prepend-icon="mdi-linkedin"
							href="https://www.linkedin.com/in/vazir-galiev-462364261/"
							target="blank"
							>Linkedin</v-btn
						>
						<v-btn
							class="mr-6 mb-6"
							prepend-icon="mdi-instagram"
							href="https://www.instagram.com/galiev.dev/"
							target="blank"
							>Instagram</v-btn
						>
						<v-btn
							class="mr-6 mb-6"
							prepend-icon="mdi-telegram"
							href="https://t.me/vgaliev4"
							target="blank"
							>Telegram</v-btn
						>
					</v-container>
				</v-card>
				<v-divider></v-divider>
			</v-container>
		</v-container>
	</v-main>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import axios from 'axios'
import { computed } from 'vue'
import { useDisplay } from 'vuetify'

export default defineComponent({
	data() {
		return {
			projects: [],
		}
	},
	async mounted() {
		await axios
			.get('https://api.modrinth.com/v2/user/galievdev/projects')
			.then(response => {
				this.projects = response.data
			})
	},
	setup() {
		const { name } = useDisplay()

		const size = computed(() => {
			// name is reactive and
			// must use .value
			switch (name.value) {
				case 'xs':
					return 220
				case 'sm':
					return 240
				case 'md':
					return 340
				case 'lg':
					return 340
				case 'xl':
					return 440
				case 'xxl':
					return 540
			}

			return undefined
		})
		return { size }
	},
})
</script>
