<template>
	<div class="index">
		<div class="">
		<router-link to='/home'>
			<img src="../assets/icon_home_select@2x.png" @click="alert(1)"/>
		</router-link>
		<router-link to='/integral'>积分</router-link>
		<router-link to='/shopcar'>购物车</router-link>
		<router-link to='/mine'>我的</router-link>
		</div>
		<router-view></router-view>
	</div>
</template>

<script>
	export default({
		name: 'index',
		data () {
			return {
				
			}
		},
		methods: {
			alert () {
				alert(1)
			}
		}
	})
</script>

<style scoped>
</style>