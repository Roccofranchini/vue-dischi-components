<template>
	<div class="col-2">
		<select v-model="select" name="" id="" class="" @change="selectSearch">
			<option selected>All</option>
			<option v-for="(type, index) in selectTypes" :key="index">{{
				type
			}}</option>
		</select>
	</div>
</template>

<script>
export default {
	name: "Select",
	data() {
		return {
			select: "",
		};
	},
	methods: {
		selectSearch() {
			this.$emit("filtering", this.select);
		},
	},
	props: ["selectTypes"],
};
</script>

<style scoped lang="scss"></style>
