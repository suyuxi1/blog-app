<template>
	<div class="xu-row">
		<div class="xu-col-8">
			<div class="xu-row">
				<div class="xu-col-12" v-for="(article, index) in articles" :key="index">
					<div class="box xu-sub-title">
						<p>{{article.title}}</p>
						<p>
							<img :src="article.avatar" class="">
						</p>
					</div>
				</div>
			</div>		
		</div>
		<div class="xu-col-4">
		
		</div>
		
	</div>
</template>

<script>
	export default {
		data(){
			return{
				articles:[]
			};
			
		},
		created(){
			this.axios.get("http://277u26362p.zicp.vip:23906/api/article").then(res =>{
				console.log(res.data.data);
				this.article = res.data.data;
			});
		},
		methods:{
			
		},
		computed:{
			
		}
	}
</script>

<style scoped>
	
</style>
