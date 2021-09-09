<template>
	<div class="col-2">
		<select v-model="select" name="" id="" class="">
			<option value="" selected>All</option>
			<option value="">pepp</option>
			<option value="">papp</option>
			<option value="">popp</option>
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
};
</script>

<style scoped lang="scss"></style>
