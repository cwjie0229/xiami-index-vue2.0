<template>
	<div class="header-wrap">
		<h2 class="title">{{title}}</h2>
	</div>
</template>

<script>
export default {
	data () {
		return {
		}
	},
	props: {
		title: {
			require: true,
			type: String
		}
	}
}
</script>

<style>
.header-wrap {
	position: relative;
	
}
.header-wrap  .title {
		margin: 0;
		font-size: 22px;
		font-weight: 200;
		line-height: 58px;
		color: #333;
	}
</style>
