<template>

        <nav class="navbar navbar-expand-sn navbar-dark bg-dark">
            <img class="img" src="../assets/images/image_post_logo copy.jpg" alt="Logo" height="40px">
            <router-link class="navbar-brand" href="#" to="/">Home</router-link>
            <router-link class="car text-white" to="/basket">
                <!-- <p class="text">TOTAL ITEMS:</p> -->
                <svg xmlns="http://www.w3.org/2000/svg" width="36" height="36" fill="currentColor" class="bi bi-cart2" viewBox="0 0 16 16">
  <path d="M0 2.5A.5.5 0 0 1 .5 2H2a.5.5 0 0 1 .485.379L2.89 4H14.5a.5.5 0 0 1 .485.621l-1.5 6A.5.5 0 0 1 13 11H4a.5.5 0 0 1-.485-.379L1.61 3H.5a.5.5 0 0 1-.5-.5zM3.14 5l1.25 5h8.22l1.25-5H3.14zM5 13a1 1 0 1 0 0 2 1 1 0 0 0 0-2zm-2 1a2 2 0 1 1 4 0 2 2 0 0 1-4 0zm9-1a1 1 0 1 0 0 2 1 1 0 0 0 0-2zm-2 1a2 2 0 1 1 4 0 2 2 0 0 1-4 0z"/>
</svg>
            </router-link>
            
    <div class="dropdown">
        <button class="btn btn-danger dropdown-toggle" type="button"
        @click.stop.prevent="toggle()"
        >Options
        <span class="caret"></span></button>
        <ul v-show="isOpen" class="dropdown-menu" style="background-color:rgb(255, 180, 180)">
            <li><router-link href="#" style="color:white" to="/login">Login</router-link></li>
            <li><router-link href="#" style="color:white" to="/register">register</router-link></li>
            <li><router-link href="#" style="color:white" to="/myorders">my orders</router-link></li>
        </ul>
    </div>

        </nav>

            

        <!-- </nav> -->

</template>

<script>

export default {

    data(){
        const getUser = this.$store.getters['user/getUser'];
        const _UserLoggedIn = getUser.id != undefined;
        return{
            isOpen: false,
            userLoggedIn:_UserLoggedIn,

            user:{
                id: getUser.id,
                name: getUser.name,
                email: '',
                session_id: ''
            },
        }
    },

    methods: {	
            toggle() {
                this.isOpen = !this.isOpen;
            },
     },
    // computed: {
        
    // },
}

</script>

<style scoped>
/* .text{
    text-decoration: none;
    text-align:start;
} */
.car{
    padding-inline: 10px;
}
.img{
    margin-left: 5px;
    margin-right: 10px;
}
.navbar-brand{
    display: block;
    margin-right: auto;
}


.dropdown-menu {
    
    /* list-style: none; */
    font-family: Arial, Helvetica, sans-serif;
    display: block;
    /* background: #eb6c65; */
    /* border: 1px #363a43 solid; */
    border-radius: 0.5em;
    
    
    /* box-shadow: 0 0.5em 1em rgba(0, 0, 0, 0.2);
    border-radius: 0.5em;
    color:red;
    position: absolute;
    top: 3em;
    left: 67%;
    transform: translateX(-80%);
    size: 5em;
    block-size: 5em 5em; */
    
    

}
.dropdown-menu li router-link{
    text-decoration: none;
    margin-left: 1ch;
    margin-top: 0;
    font-size: 18px;

}
/* .dropdown-menu li a:hover{
    display: block;
    background: rgba(152, 3, 3, 0.067);

} */

/* navbar-expand-sn navbar-dark bg-dark{
font-size: 45px;

line-height: 1.428;
} */

/* *{
    padding: 0;
    margin-bottom: 0;
    margin-right: 350px;
    font-family: sans-serif;
} */
/* ul.bottondrop{
    list-style: none;
    background: #112C66;
    margin-left: auto;
}  */

/* ul.bottondrop li{
    display: inline-block;
    position: relative;
}

ul.bottondrop li a {
    display: block;
    position: 20px 25px;
    color: #FFF;
    text-decoration: none;
    text-align: center;
    font-size: 20px;
}

ul.bottondrop li ul.dropdown li{
    display: block;
}
ul.bottondrop li ul.dropdown{
    width: 100%;
    background: #22438C;
    position: absolute;
    z-index: 9990;
    display:none;
}
ul.bottondrop li a:hover{
    background: #112C66;
}
ul.bottondrop li:hover ul.dropdown{
    display: block;

    
} 

ul.bottondrop{
    padding: 0; 
    margin: 0;
    list-style: none;
    background: #112C66;
    margin-left: auto;
    margin-top: auto;
    font-family: sans-serif;
} 

ul.bottondrop li{
    display: inline-block;
    position: relative;
}

ul.bottondrop li a {
    display: block;
    position: 100px 100px;
    color: rgb(219, 20, 20);
    text-decoration: none;
    text-align: auto;
    font-size: 20px;
} */


</style>



