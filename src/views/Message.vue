<template>
	<div class="bg">
		<div class="cenas">
			<h1 class="message">{{message}}</h1>
		</div>
			<!-- <h1 class="message">x</h1> -->
		
	</div>

</template>

<script>
export default {
    data() {
		return {
            message: '',
		}
	},   
    mounted() {
		this.setMessage()

	},

	methods:{
		setMessage(){
				if (this.$route.params.id == 1) {
                this.message = "Item remove!!"
                }
				if (this.$route.params.id == 2) {
                this.message = "Welcome! You can now login"
                }
				if (this.$route.params.id == 3) {
                this.message = "Welcome back " + this.$store.getters['user/getUser'].name + "!"
                }
				if (this.$route.params.id == 5) {
                this.message = "Your product was add to the cart!"
                }	
				if (this.$route.params.id == 6) {
                this.message = "you have to login!!"
                }	
				if (this.$route.params.id == 7) {
                this.message = "Thank you see you next time!!"
                }	
																		
			
				var timeleft = 2;
				var downloadTimer = setInterval(() => {
					if(timeleft <= 0){
						clearInterval(downloadTimer)
						this.$router.push('/')
					}
				timeleft -= 1
				}, 1000)
		}
	}

}
</script>

<style scoped>

.bg{
	
    background-image: url("../assets/images/back2.png");
	background-size: cover;
	padding-top: 250px;
	/* padding: auto; */
    width: auto;
	top: auto;
    height: 700px; 
}


.cenas{
	background-color:rgb(119, 119, 134);
	padding: 15px;
	margin: 10px;
	width: auto;
	height: 150px;
}
.message{
	font-family:Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
	padding: 2.3%;
	text-align: center;
	color: white;
}

</style>



