<template>
    <div class="bg">
    <Header />
    <div class="contflex">
        
            <tr v-for="product in products" :key="product.id" >
            <div  class="card">
                
                    <!-- <img class="img" src="../assets/images/corda.png"  style="width:100%"> -->
                <img class="img" :src="require(`@/assets/images/${product.image}`)" alt="Avatar" style="width:100%">
                <div class="container">
                    <h4><b>{{product.name}}</b></h4> 
                <p>{{product.description}}. </p>
                <p>The cost is {{product.price}}€</p>
                    <div class="class-flex">
                        <div class="input-group">
                            <div class="input-group-prepend">
                                <span class="input-group-text">Quantity</span>
                            </div>
                            <input type="number" class="form-control"/>
                        </div>
                    </div>
                    <form @submit.prevent="addToCart(product.id)">
                    <button class="btn btn-danger " type="submit">Add to cart
                        <!-- <router-link  
                        style="color:white" >
                        Add to cart</router-link> -->
                    </button>
                </form>
                </div>
            
            </div>
        </tr>
    
    </div>
    
    
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
                userLoggedIn: this.isloggedin(),
                text:"",
                error:false,
            }
        },
    
        mounted() {
        },
        methods: {
            isloggedin() {
			console.log(this.$store.getters['user/getUser']);
			console.log(this.$store.getters['user/getUser'].id);
			return this.$store.getters['user/getUser'].id != undefined;
		},

            async addToCart(id){
                if(this.userLoggedIn){console.log(this.$store.getters['user/getUser']);
                
                const addProduct =  this.$store.commit('basket/incrementProduct', id);
                
                if(addProduct){
                    console.log(id);
                    this.$router.push({path:'/message/5'})
                }
                }
                else{
                    this.$router.push({path:'/message/6'})
                }
            }
        
        },
        computed: {
    
        },
    
        created: async function(){
            const getProduct= await this.$store.dispatch('products/getProductsFromDB');
            if(getProduct){
                this.products = this.$store.getters['products/getProducts'];
                console.log(this.products);
            }
        }
    }
    </script>
    
    <style scoped>

    .contflex{
        display: grid;
        width: 100%;
        grid-template-columns: 1fr 1fr 1fr;
    }
    .bg{
        background-color: rgb(71, 70, 70);
        /* background-image: url("../assets/images/back2.png"); */
        background-size: cover;
        width: auto;
        height: auto; 
        
    }
    
    .card{
        /* border:5px cyan solid; */
        /* display: inline-block; */
        margin: 10px;
        background-color: white;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        
        /* width: 22%; */
        /* height: 200px; */
        border-radius: 5px;
    }
    
    .card:hover {
      box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
    }
    
    
    .btn{
        display: block;
        margin: 4px;
        margin-left: 180px;
        
    }
    
    /* .container {
      padding: 2px 16px;
      
    } */
    
    .img{
        border-radius: 5px 5px 0 0;
    }
    
    
    </style>