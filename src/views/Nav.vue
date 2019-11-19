<template>
	<div>
		<div class="su-nav su-fx-between">
			<ul class="ul-left su-fx-around">
				<li><router-link to="/">主页</router-link></li>
				<li><router-link to="/c">专题</router-link></li>
				<li><router-link to="/p">文章</router-link></li>
				<li><router-link to="/u">作者</router-link></li>
			</ul>
			<ul class="su-fx-right ul-right ">
				<ul class="su-fx-around right-box" v-if="!this.user">
					<li><router-link to="">下载APP</router-link></li>
					<li><router-link to="/sign">登录</router-link></li>
				</ul>
				<ul class="su-fx-around" v-if="this.user">
					<div class="box">
						<router-link to="/userDetaile"><img :src="user.avatar"></router-link>
					</div>
					<div class="box su-btn"><span @click="logout()" >退出</span></div>
				</ul>
			</ul>
		</div>
		<router-view class="su-container container" />
		
		<footer></footer>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				user : JSON.parse(localStorage.getItem('user'))
			}
		},
		
		methods: {
			logout() {
				// localStorage.setItem('user',this.user)
				alert('tuichu')
				this.user = null
			}				
		}
	}
</script>

<style scoped>
.container {
	/* height: 100%; */
	background-color:#AAAAAA;
}
ul{
	display: flex;
}
.ul-left {
	width: 50%;
	height: 100%;
	

}
.ul-right{
	width: 25%;
	height: 100%;
	justify-content: space-between;
	background-color: #42B983
}
li{	
	font-size: 25px;
	font-weight: 800;
	color: cadetblue;
}
.right-box{
	width: 100%;
	height: 100%;
}
.box{
	width: 30%;
	height: 80%;
	align-content: center;
	font-size: 25px;
	font-weight: 800;
	/* background-color: #A9A9A9 */
}
img{
	width: 90%;
	border-radius: 50%;
}

</style>
