<template >
	<div class="bg">
		<Header/>
		
		<div class="texto" >
			<h1 class="title" style="color: rgb(180, 0, 0);">WELCOME TO GYMSTORE</h1>
			<h1 class="descricao1" style="color:white">Here you can by any product</h1>
            <h1 class="descricao2" style="color:white">to </h1>
            <h1 class="descricao3" style="color:white">elevate your performance</h1>
			<div>
				<button class="btn btn-danger" type="button">
					<router-link to="/products" 
					style="color:white">
					Produts</router-link>
				</button>
			</div>
		</div>

		<Footer/>
  </div>
  

</template>

<script>
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'

	export default {
		components: {
			Header,
			Footer,
			
		}
	}
</script>

<style scoped>
	#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 100px;
	}
	.title{
		
        font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
        margin-left: 60px;
        margin-top:150px;
		
	}
    .descricao1{
		font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
        font-size: large;
        margin-left: 160px;
       
	}
	.descricao2{
		font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
        margin-left: 280px;
		font-size: large
       
	}
	.descricao3{
		font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
        font-size: large;
        margin-left: 170px;
       
	}
	.bg{
	
    background-image: url("../assets/images/back2.png");
	background-size: cover;

    width: auto;
    height: 700px; 
}

.btn{
	margin-left:260px;
	margin-top: 30px;
}


	

</style>