<template>
<div class="userprofile">
<h1> {{msg}} </h1>
<form class="container">
            
                <router-link to="/neworder" exact> NEW_ORDER </router-link>
       
                <router-link to="/orderhistory" exact> ORDER_HISTORY </router-link> 

                <button type="button" v-on:click="logout()"> USER LOG-OUT </button>
             
</form>
</div>
</template>

<script>
export default {
    name:'userprofile',
    data: function(){
        return{
            msg:"----- Hello User,'B' Gift cards Welcomes to Profile -----",
            up:"userName"
        }
    },
    methods:{
        logout(){
             this.$router.push({path:'/login'})
            console.log("User Logging Off")
        }
    }
   
}


</script>

<style scoped>

.router-link-active{
    background-color: lightgrey;
    color:black;
}

li{
    display: inline-block;
    margin: 10px;
    padding: 10px;

}


ul{
    list-style-type: none;

}

.container {
  padding: 16px;
  
}
input[type=text] {
  width: 25%;
  padding: 10px;
  margin: 5px 0 22px 0;
 /* display: inline-block; */
  border: none;
  background: #ebebe0;
   float:center;
  align-content: left;
}

button {
  background-color:#666699;
  color: white;
  padding: 10px;
  margin: 5px 0 22px 0;
  border: none;
  cursor: pointer;
  width: 18%;
  opacity: 0.9;
  margin-left:30%;
  
}
button:hover {
  opacity:1;
}
</style>