<template>
	<header class="mb-5">
		<div class="container">
			<img src="../assets/img/logo.png" />
		</div>
	</header>
</template>

<script>
export default {
	name: "Header",
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
	}
}
</style>
