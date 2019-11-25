<template>
	<div>
		<h2>user</h2>
		<div class="su-col-3 container">
			
		</div>
	</div>
		
</template>

<script>
	export default {
		data(){
			return{
				users : [],
			};
		},
		created(){
			this.axios.get(this.GLOBAL.baseUrl + '/user', { responseType: 'blob' }).then(res => {
				// console.log(res);
				this.users = res.data.data;					
			});
		},
		methods:{
			
		},
		computed:{
			
		}
	}
</script>

<style scoped> 
	h2{
		color: #42B983;
		font-size: 50px;
	}
	.container{
		background-color: #fff;
	}
</style>
