<template>
<div class="bg">


  
<Header />
	<div class="container" >
		<h2 class="center">Login</h2>
		<form @submit.prevent="login">

			<div class="form-group">
				<label class="center" for="email">Email:</label>
				<input v-model="user.email" type="email" class="form-control" id="email" placeholder="Enter email" name="email">
			</div>
			<div class="form-group">
				<label class="center" for="pwd">Password:</label>
					<input v-model="user.password" type="password" class="form-control" id="pwd" placeholder="Enter password" name="pswd">
			</div>
			<div class="form-group form-check">
				<label style="color: white" class="form-check-label">
					<input class="form-check-input" type="checkbox" name="remember"> Remember me
				</label>
			</div>
		<button type="submit" class="btn" >Submit</button>

		</form>
	</div>

<Footer />

</div>
</template>
<script>
import Footer from '@/components/Footer.vue'
import Header from '@/components/Header.vue'


export default {
	components: {
		Footer,
        Header,
		
	},   
	data() {
      return {	
        user: {
			email: '',
			password: '',
        },
		submitting: false,
		error: false,
      }
    },
	
	methods: {
		async login(){
			const canlogin = await this.$store.dispatch('user/loginUser',this.user);
			if(canlogin){
				this.$router.push({ path: '/message/3'});
			}
			else this.error=true;
		}
	},
	
	computed: {

	},
	directives: {

	},
	created: function () {

	}
}
</script>
<style scoped>
.container{
	display: block;
	border-radius: 0.5em;
	background-color:rgb(163, 144, 144);
	margin-top: 10%;
	margin-bottom: 10%;
}

.btn{
	background-color:rgb(189, 57, 57);
}
.center{

}

.bg{
	
    background-image: url("../assets/images/back2.png");
	background-size: cover;
    width: auto;
    height: 700px;
}

</style>