<template>
	<div class="regist">
		<img class="logo_img" src="@/assets/Bar@2x.png"/>
		<div class="til">
			互助商城
		</div>
		<div class="com">
			<div class="int_fle">
				<img src="@/assets/phoneicon@2x.png"/>
				<input type="text" name="" id="" v-model="phone" placeholder="请输入手机号"/>
				<img src="@/assets/shanchu.png" v-if="phone" @click="phone = ''"/>
			</div>
			<div class="int_fle">
				<img src="@/assets/yzmicon@2x.png"/>
				<input type="text" name="" id="" v-model="code" placeholder="请输入验证号"/>
				<img src="@/assets/shanchu.png" v-if="code" @click="code = ''"/>
				<p class="getcode opt5" v-if="show && !codeshow">获取验证码</p>
	            <p class="getcode" v-if="show && codeshow" @click="getCode">获取验证码</p>
	            <p class="getcode opt5" v-if="!show">{{count}}s后获取</p>
			</div>
			<div class="int_fle">
				<img src="@/assets/tjicon@2x.png"/>
				<input type="text" name="" id="" v-model="people" placeholder="请输入推荐人"/>
				<img src="@/assets/shanchu.png" v-if="people" @click="people = ''"/>
			</div>
			<p class="link_p">已注册？<router-link to='/login'>快速登录</router-link></p>
		</div>
		<div class="reg" v-if="phone && code && people" @click="regClick">
			立即注册
		</div>
		<div class="reg opt5" v-else>
			立即注册
		</div>
	</div>
</template>

<script>
	import { Toast } from 'vant'
	import qs from 'qs'
	export default({
		name: 'regist',
		data () {
			return {
				show: true,					//显示获取
			 	count: '',					//倒计时
			 	timer: null,				//倒计时事件
			 	codeshow: false,			//否不可点击
				phone:'',
				code: '',
				people: ''
			}
		},
		methods: {
			// 获取验证码
		    getCode () {
		        let that = this
		        Toast('获取成功')
	          	that.codeGet()
	          	return false
		        that.$axios({
		      	  	url: '/leaderapi/sendVerifyCode.action',
		       		method: 'POST',
		        	data: qs.stringify({
		          		mobile: that.phone
		        	})
		      	}).then(res => {
			        if (res.data.status === '0') {
			          	Toast('获取成功')
			          	that.codeGet()
			        } else {
			          	Toast(res.data.message)
			        }
		      	})
		    },
		    //倒计时
		    codeGet () {
		        const TIME_COUNT = 60
		        let that = this
		        that.count = TIME_COUNT
		        that.show = false
		        that.timer = setInterval(() => {
		        if (that.count > 0 && that.count <= TIME_COUNT) {
		          	that.count--
		        } else {
		            that.show = true
		            clearInterval(this.timer)
		            that.timer = null
		        }
		      }, 1000)
		    },
		    //提交
		    regClick () {
		    	let that = this
		        that.$axios({
		      	  	url: '/leaderapi/sendVerifyCode.action',
		       		method: 'POST',
		        	data: qs.stringify({
		          		phone: that.phone,
		          		code: that.code,
		          		people: that.people
		        	})
		      	}).then(res => {
			        if (res.data.code == 0) {
			        	Toast(res.data.message)
			        } else {
			          	Toast(res.data.message)
			        }
		      	})
		    }
		},
		watch: {
			phone () {
				if (this.phone) {
					this.codeshow = true
				} else {
					this.codeshow = false
				}
			}
		}
	})
</script>

<style scoped>
.regist{overflow: hidden;height: 100%;background: #fff;}
.opt5{opacity: .5;}
.logo_img{width: 1.8rem;height: 1.8rem;display: block;margin: auto;margin-top: 1.36rem;}
.til{text-align: center;font-size: .32rem;color: #666666;}
.com{margin: 1.2rem .74rem .5rem .74rem;}
.int_fle{display: flex;align-items: center;border-bottom: .02rem solid #bbbbbb;padding: .2rem 0;margin-bottom: .28rem;}
.int_fle input{margin-left: .2rem; width: 100%;font-size: .3rem;border: 0;}
.getcode{color: #FE7113;font-size: .3;white-space: normal;width: 50%;text-align: right;}
.link_p{color: #FE7113;font-size: .3rem;text-align: right;}
.link_p a{border-bottom: 1px solid #FE7113;padding-bottom: 2px;color: #FE7113;}
.reg{background-image: linear-gradient(-90deg, #FF9400 0%, #FF6808 100%);border-radius: .44rem;margin: .48rem .74rem;text-align: center;height: .88rem;line-height: .88rem;color: #fff;}
</style>