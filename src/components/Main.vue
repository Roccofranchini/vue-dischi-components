<template>
	<main class="container">
		<section id="album-container" class="my-5 py-5">
			<CardAlbum
				v-for="(album, index) in filteredAlbums"
				:key="index"
				:album="album"
			/>
		</section>
	</main>
</template>

<script>
import CardAlbum from "./CardAlbum.vue";

export default {
	name: "Main",
	components: {
		CardAlbum,
	},
	props: ["albums", "select"],
	methods: {},
	computed: {
		filteredAlbums() {
			const selectedType = this.select;
			return this.albums.filter((album) => album.genre.includes(selectedType));
		},
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
