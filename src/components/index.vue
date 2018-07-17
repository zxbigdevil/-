<template>
	<div class="index">
		主页底部导航
		<div class="">
		<router-link to='/home'>首页</router-link>
		<router-link to='/integral'>积分</router-link>
		<router-link to='/shopcar'>购物车</router-link>
		<router-link to='/mine'>我的</router-link>
		</div>
		<router-view></router-view>
	</div>
</template>

<script>
	export default({
		name: 'index'
	})
</script>

<style scoped>
</style>