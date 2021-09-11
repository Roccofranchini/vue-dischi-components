<template>
	<header class="mb-5">
		<div class="container-fluid">
			<div class="row justify-content-between">
				<img src="../assets/img/logo.png" />
				<Select :selectTypes="selectTypes" @filtering="search" />
			</div>
		</div>
	</header>
</template>

<script>
import Select from "./Select.vue";

export default {
	name: "Header",
	data() {
		return {
			select: "",
		};
	},
	components: {
		Select,
	},
	props: ["albums"],
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
	methods: {
		search(selectedType) {
			this.$emit("filtering", selectedType);
		},
	},
};
</script>

<style scoped lang="scss">
header {
	background-color: #32462e;
	height: 70px;
	padding: 10px;
	position: fixed;
	z-index: 1;
	top: 0;
	left: 0;
	width: 100%;
	img {
		height: 50px;
		width: auto;
	}
}
</style>
