<template>
	<div>
		<div class="su-nav su-fx-between">
			<ul class="ul-left su-fx-around">
				<li><router-link to="/">主页</router-link></li>
				<li><router-link to="/c">专题</router-link></li>
				<li><router-link to="/p">文章</router-link></li>
				<li><router-link to="/u">作者</router-link></li>
			</ul>
			<div class="su-fx-right">
				<ul class="ul-right su-fx-around" v-if="!this.user">
					<li><router-link to="">下载APP</router-link></li>
					<li><router-link to="/sign">登录</router-link></li>
				</ul>
				<ul>
					<li v-if="this.user" class="ul-right su-fx-right">
						<router-link to="/user"><img :src="user.avatar" class="su-avatar-normal" /></router-link>
					</li>
				</ul>
			</div>
		</div>
		<router-view class="su-container container" />
		
		<footer></footer>
	</div>
</template>

<script></script>

<style scoped>
.container {
	height: 500px;
	background-color: #4caf50;
}
.ul-left {
	width: 55%;
	height: 60px;

}
.ul-right{
	width: 300px;
	height: 60px;
	background-color:#009688;
}
li{
	
	font-size: 20px;
	font-weight: bold;
}
</style>
