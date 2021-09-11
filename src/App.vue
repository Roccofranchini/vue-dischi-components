<template>
	<div id="app">
		<Header :albums="albums" @filtering="search" />
		<Main :albums="albums" :select="select" />
	</div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import axios from "axios";

export default {
	name: "App",

	components: {
		Header,
		Main,
	},
	data() {
		return {
			albums: [],
			select: "",
		};
	},
	methods: {
		search(selectedType) {
			this.select = selectedType;
		},
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

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";
@import "@/assets/scss/style.scss";
</style>
