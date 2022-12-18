<template>
<div class="bg">
<Header />
<div class="container1" >

	<tr v-for="product in products" :key="product.id" >
		<div class="card" v-if="product !== null">
			<img class="img" :src="require(`@/assets/images/${product.image}`)" alt="logo" style="width:200px">
			<p class="title">{{product.name}}</p>
			<p class="price">cost {{product.price}}€</p>
			
			<button @click="removeToCart(product.id)" class="btnremove" type="submit">remove</button>
	</div>
	</tr>
		
</div>
<button class="btn btn-danger" type="button">
			<router-link to="/products" 
					style="color:white">
					add Produts</router-link></button>
					
			<button id="bt1" @submit.prevent="removeToCart()" class="btnremove" type="remove">remove all</button>
<!-- <div class="card" style="background-color:#ffffff;">
  <div class="bg-image hover-overlay ripple" data-mdb-ripple-color="light">
    <img src="../assets/images/logo.png" alt="Avatar" style="width:100%"/>
    <a href="#!">
      <div class="mask" style="background-color: rgba(251, 251, 251, 0.15)"></div>
    </a>
  </div>

  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <button type="button" class="btn btn-primary">Button</button>
  </div>
</div> -->


<Footer />

</div>
</template>

<script>

import Footer from '@/components/Footer.vue'
    import Header from '@/components/Header.vue'

    
    export default {
        name: 'products',
        components: {
            Footer,
            Header,
        },
        data() {
            return {
                products: [],
            }
        },
    
        mounted() {
        },
        methods: {

			async removeToCart(id){
				console.log("this.products-1");
                console.log(this.products);
                await this.$store.commit('basket/decrementProduct', id);
				this.products=this.$store.getters['basket/getProducts'];
				console.log("this.products-2");
				console.log(this.products);

                
              
            },


        },
        computed: {
    
        },
		
    
        created:  function(){
            const getProducts= this.$store.getters['basket/getProducts'];
        
				for (let index = 0; index < getProducts.length; index++) {
					this.products.push(this.$store.getters['products/getProduct'](getProducts[index].id.toString()));
					console.log(this.products[index]);
				}
        }
    }
</script>

<style scoped>
.bg{
	
    background-color: rgb(71, 70, 70);
	background-size: cover;
    width: auto;
    height: auto; 
}

.container1{
	display: grid;
	grid-template-columns: 1fr ;
	background-color: rgb(146, 146, 146);
	height: auto;
	width: 900px;
	margin-top: 10%;
	margin-left: 20%;
	margin-right: 20%;
	
	border-radius: 5px;
}
.card{
	margin: 10px;
	display: inline-block;
	background-color: white;
	border-radius: 5px;
	width: 800px;
}

.btn{
	margin-left:30%;
	margin-top: 20px;
	margin-bottom: 50px;
}
.btn2{
	margin-left:20%;
	margin-top: 10px;
	margin-bottom: 50px;
	border-radius: 5px;

}

.title{
	display:flex;
	margin-left: 250px;
	
	align-self: flex-end;
	/* margin-bottom:110px; */
	margin-bottom: 20px;
	margin-top:-45px;
	
}

.btnremove{
	margin-left: 700px;
	margin-bottom: 10px;
	width: 80px;
	color:white;
	background-color: brown;
	border-radius: 5px;
}

.price{
	margin-left: 20px;
}

#bt1{
	margin-left:50px
}

</style>