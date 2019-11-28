<template>
	<div class="su-container">
		<h2>user</h2>
		<div class="su-col-3 su-fx-around">
			<div class="card su-fxc-top su-shadow" v-for="(user,index) in users" :key="index">
				<div class="head su-fx-center">
					<div class="img su-btn">
						<!-- <img src="http://pic27.nipic.com/20130313/9252150_092049419327_2.jpg"> -->
						<img :src="user.avatar">
					</div>
				</div>
				<div class="mid su-fx-center">
					<!-- <span class="name">name收到就好vjh</span> -->
					<span class="name">{{user.nickname}}</span>
					<br>
					<!-- <span class="address">来自： 尽快发货等各方面小仓库发噶复健科</span> -->
					<span class="address">来自：{{user.address}}</span>
					<br>	
					<!-- <span class="introduction">简介： 十块很快接一天月日鳄鱼计法蒂冈咖啡馆</span>	 -->
					<span class="introduction">{{user.introduction}}</span>	
				</div>
				<div class="end su-fx-around">
					<div class="data su-fx-around">
						<!-- <span class="su-btn">111111篇文章</span> -->
						<span class="su-btn">{{user.articles}}篇文章</span>
						<!-- <span class="su-btn">111111个粉丝</span> -->
						<span class="su-btn">{{user.fans}}个粉丝</span>
						<!-- <span class="su-btn">111111个关注</span> -->
						<!-- <span class="su-btn">111111个关注</span> -->
						<span class="su-btn">{{user.follows}}个关注</span>
					</div>
					<div>
						<span class="buttom su-btn">个人中心</span>
					</div>
					
				</div>
				
			</div>
		
		</div>
		<div class="row su-fx-center">
			<button class="btn su-btn" @click="loadMore">点击加载更多</button>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			users: [],
			currentPage: 1,
			count: 6
		};
	},
	created() {
		this.axios
			.get(this.GLOBAL.baseUrl + '/user', {
				params: {
					page: this.currentPage,
					count: this.count
				}
			})
			.then(res => {
				console.log(res.data.data.length);
				this.users = res.data.data;
			});
	},
	methods: {
		loadMore() {
			this.currentPage = this.currentPage + 1;
			this.axios
				.get(this.GLOBAL.baseUrl + '/user', {
					params: {
						page: this.currentPage,
						count: this.count
					}
				})
				.then(res => {
					console.log(res.data.data.length);
					let temp = [];
					temp = res.data.data;
					for (var i = 0; i < temp.length; i++) {
						this.users.splice(this.currentPage * this.count, 0, temp[i]);
					}
					console.log(this.users.length);
				});
		},
		go(page) {
			window.location.href = page;
		}
	}
};
</script>

<style scoped>
.su-container {
	/* height: 500px; */
	background-color: #dddddd;
}
.su-col-3 {
	flex-wrap: wrap;
}
.card {
	flex: 0 0 30%;
	width: 24%;
	height: 400px;
	margin: 50px 10px 80px 10px;
	/* border: 1px; */
	border-radius: 10%;
	background-color: rgb(255, 250, 232);
	/* 内边距 */
	padding: 10px 10px 20px 10px;
	 /* background-image: url(http://pic.616pic.com/bg_w1180/00/03/67/8me157uzTA.jpg); */
}
.head{
	width: 99%;
	height: 40%;
	/* border: 1px solid #FB8C00; */
	margin-top: -80px;
	
}
.img {
	width: 35%;
	height: 100%;
	/* border: 1px solid #42b983; */
}
.img img{
	width: 100%;
	height: 100%;
	border-radius: 50%;
	/* border: 1px solid chocolate; */
}
.mid{
	width: 99%;
	height: 50%;
	/* border: 1px solid coral; */
	flex-direction: column;
	padding: 20px 20px 20px 20px;
}
.name{
	font-size: 25px;
	font-weight: bold;
}
.address{
	font-size: 17px;
	font-weight: 600;
	opacity: 0.5;
}
.end{
	width: 99%;
	height: 30%;
	margin-bottom: 0;
	/* border: 1px solid cadetblue; */
	flex-direction: column;
}
.data{
	width: 100%;
	height: 50%;
	/* border: 1px solid #DEB887; */
}
.buttom {
	font-size: 27px;
	font-weight: bold;
	opacity: 0.6;
	
}
.row{
	width: 100%;
	height: 50px;
	/* border: 1px solid #DEB887; */
}
.btn{
	width: 35%;
	height: 100%;
	font-size: 20px;
	border-radius: 10px;
	background-color: #A9A9A9;
}
</style>
