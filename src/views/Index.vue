<template>
	<div class="su-row">
		<div class="su-col-8">
			<div class="card su-fx-around" v-for="(article, index) in articles.slice(20, 30)" :key="index">
				<div class="img"><img :src="article.picture" alt="" /></div>
				<div class="contant">
					<div class="head su-fx-center su-title">
						<span>{{ article.author }}</span>
						<!-- <span>{{article.create_time}}</span> -->
					</div>
					<p class="article">{{ article.introduction }}</p>
				</div>
			</div>
		</div>
		<div class="su-col-4"></div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			articles: []
		};
	},
	created() {
		this.axios.get('http://localhost:8080/api/article').then(res => {
			console.log(res.data.data);
			this.articles = res.data.data;
			for (var i = 0; i < this.articles.length; i++) {
				this.articles[i].picture = this.getImage(this.articles[i].picture);
			}
		});
	},
	methods: {
		getImage(url) {
			return 'https://images.weserv.nl/?url=' + url;
		}
	},
	computed: {}
};
</script>

<style scoped>
.su-row {
	/* height: 800px; */
}
.su-col-8 {
	width: 100%;
	height: 100%;
	display: flex;
	align-items: center;
	flex-direction: column;
	background-color: #42b983;
}
.card {
	width: 87%;
	height: 230px;
	display: flex;
	/* background-color: #DEB887; */
	border: 2px solid #ff0000;
	margin: 4%;
	display: flex;
}
.img {
	width: 25%;
	height: 90%;
	/* border: 2px solid #ff0000; */
}
.img img {
	width: 100%;
	height: 100%;
	border-radius: 10px;
}
.article{
	padding: 10px;
}
.contant {
	width: 70%;
	height: 90%;
	border: 2px solid #ff0000;
}

.su-col-4 {
	background-color: #deb887;
}
</style>
