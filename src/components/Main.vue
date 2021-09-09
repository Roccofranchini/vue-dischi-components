<template>
	<main class="container">
		<div class="row justify-content-center">
			<Select />
		</div>
		<section id="album-container" class="my-5 py-5">
			<CardAlbum v-for="(album, index) in albums" :key="index" :album="album" />
		</section>
	</main>
</template>

<script>
import axios from "axios";
import CardAlbum from "./CardAlbum.vue";
import Select from "./Select.vue";

export default {
	name: "Main",
	components: {
		CardAlbum,
		Select,
	},
	data() {
		return {
			albums: [],
		};
	},
	created() {
		axios
			.get("https://flynn.boolean.careers/exercises/api/array/music")
			.then((res) => {
				const albums = res.data.response;
				this.albums = albums;
			})
			.catch(() => {
				this.error = true;
			});
	},
};
</script>

<style scoped lang="scss">
#album-container {
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
}
</style>
