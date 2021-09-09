<template>
	<main class="container">
		<div class="row justify-content-center">
			<Select :selectTypes="selectTypes" @performFilter="filterAlbums" />
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
	computed: {
		selectTypes() {
			const selectTypes = [];
			for (var i = 0; i < this.albums.length; i++) {
				console.log(this.albums[i].genre);
				if (!selectTypes.includes(this.albums[i].genre)) {
					selectTypes.push(this.albums[i].genre);
				}
			}
			console.log(selectTypes);
			return selectTypes;
		},
	},
	methods: {},
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
