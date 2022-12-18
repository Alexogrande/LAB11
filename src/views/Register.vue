<template>
<div class="bg">
	
<Header />
<Background />

	<div class="container">
		<h2 class="center" >Register</h2>
		<form @submit.prevent="register">
		<div class="form-group">
			<label class="center" for="name">Name:</label>
			<input v-model="user.name" type="name" class="form-control" id="name" placeholder="Enter name" name="name">
		</div>

		<div class="form-group">
			<label class="center" for="email">Email:</label>
			<input v-model="user.email" type="email" class="form-control" id="email" placeholder="Enter email" name="email">
		</div>

		<div class="form-group">
			<label class="center" for="pwd">Password:</label>
			<input v-model="user.password" type="password" class="form-control" id="pwd" placeholder="Enter password" name="pswd">
		</div>

		<div class="form-group">
			<label class="center" for="pwd">Confirm password:</label>
			<input v-model="passwordConfirmation" type="password" class="form-control" id="cpwd" placeholder="Confirm password" name="pswd">
		</div>
		<button class="btn" type="submit">Register</button>
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
			name: '',
			email: '',
			password: '',
        },
		passwordConfirmation: '',
		submitting: true,
		error: true,	
      }
    },
	
	methods: {
		validate(){
			var validRegex = /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/;

			if (!this.user.email.match(validRegex)) {
				this.error = true;
				return false;
			}
			else if (this.user.password !== this.passwordConfirmation) {
			
				this.error = true;
				return false;
			}
			else if (this.user.password.length < 6) {
				this.error = true;
				return false;
			}

			this.error = false;
			return true;
		},


		async register() {
			if (!this.validate()) {
				return;
			}
			const exists = await this.$store.dispatch('user/userExists', this.user);
			if(!exists) { 
				await this.$store.dispatch('user/addUser');
				this.$router.push({path: '/message/2'})
			}
		},
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