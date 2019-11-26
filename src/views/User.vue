<template>
	<div class="su-container">
		<h2>user</h2>
		<div class="su-col-3 su-fx-around">
			<div class="card">
				<div class="img">
					
				</div>
			</div>
			<div class="card"></div>
			<div class="card"></div>
			<div class="card"></div>
			<div class="card"></div>
			<div class="card"></div>
			<div class="card"></div>
			<div class="card"></div>
			<div class="card"></div>
			<div class="card"></div>
			<div class="card"></div>
			<div class="card"></div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			users: []
		};
	},
	created() {
		this.axios.get(this.GLOBAL.baseUrl + '/user', { responseType: 'blob' }).then(res => {
			// console.log(res);
			this.users = res.data.data;
		});
	},
	methods: {},
	computed: {}
};
</script>

<style scoped>
.su-container {
	/* height: 500px; */
	background-color: #dddddd;
}
.su-col-3{
	flex-wrap: wrap;
}
.card {
	margin-top: 150px;
	display: flex;
	justify-content: center;
	width: 24%;
	height: 400px;
	border: 1px solid #fb8c00;
}
.img{
	margin-top:-80px;
	width: 40%;
	height: 40%;
	border: 1px solid #42B983;
	border-radius: 50%;
}
</style>
