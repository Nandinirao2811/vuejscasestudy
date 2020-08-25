<template>

    <div class="topnav">
    <a class="active" > <img alt="B logo" src="../assets/Picture2.png"> </a>
   
 <a> <router-link to="/" exact>BLOOM_GIFT_CARDS </router-link>  </a>

<a>  <router-link to="/register" exact>REGISTER</router-link> </a>
<a>  <router-link to="/login" exact>LOG-IN</router-link> </a>
<a>  <router-link to="/admin" exact>ADMIN</router-link> </a>
    </div>
</template>

<script>
export default {
}
</script>

<style scoped>

.router-link-active{
    background-color: lightgrey;
    color: red;
}

li{
    display: inline-block;
    margin: 10px;
    padding: 10px;

}

ul{
    list-style-type: none;

}
.topnav {
  background-color:#009999 ;
  overflow: hidden;
}

.topnav a {
  float: left;
  color: black;
  text-align: center;
  padding: 10px 12px;
  text-decoration: none;
  font-size: 15px;
 
}

.topnav a:hover {
  background-color:#009999 ;
 color: white;
}

.topnav a.active {
  background-color: #009999;
  color: white;
}

</style>