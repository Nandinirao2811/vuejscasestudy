<template>
<div class="login">
<span>
<h1> {{msg}} </h1>
</span>
<form class="container">
<label> <span class="mandatory"> * </span> <b> User Name : </b> </label> 
<input type="text" placeholder="Enter User Name" v-model.lazy="login.userName" required >
 <br>
 <label> <span class="mandatory"> * </span> <b> Password : </b> </label> 

<input type="text"  placeholder="Enter User Password" v-model.lazy="login.password" required >
<br>
<button type="button"  v-on:click="LoginBloom()">Log-In</button>
      </form>
</div>
</template>
<script>
export default {
  name: 'Login',
  data: function(){
    return {
          msg:"----- Bloom Gift Cards - User Login Here -----",
          login:{
             "userName":"",
             "password": ""
             
          },
          error:[]
      }
  },
  methods:{
 LoginBloom(){
    let validLoginBloom = this.ValidateLogin()
          if(localStorage){
            localStorage.setItem("login"+this.login.id, JSON.stringify(this.login))
        }
        if(validLoginBloom){
             
   this.$http.get("http://localhost:3000/login")
   .then(res=>{
    //   console.log(this.userName, this.password)
      console.log(res)
       this.$router.push({path:'/userprofile'})
   },err=>{
     console.log(err)
   })
  }
   
 },
 ValidateLogin: function(){
   console.log("Validating User Credentials... Please Wait...")
   if(this.login.id >= 1){
     console.log("id log checking")
       this.error.push("Id must be non zero")
       return false
     }
    
        if(this.login.userName == "" && this.login.password == ""){
      //   console.log(this.login.userName, this.login.password)
       this.error.push("wrong")
       console.log("wrong credentials")
       return false
     }else{
       console.log("Welcome User ")
        console.log(this.login.userName, this.login.password)
     
     }
     
     
     return true
 }
  }


}
</script>
<style scoped>

input[type=text] {
  width: 25%;
  padding: 10px;
  margin: 5px 0 22px 0;
 /* display: inline-block; */
  border: none;
  background: #bfbfbf;
   float:center;
  align-content: left;
}

button {
  background-color:#404040;
  color: white;
  padding: 10px;
  margin: 5px 0 22px 0;
  border: none;
  cursor: pointer;
  width: 18%;
  opacity: 0.9;
  
}
button:hover {
  opacity:1;
}
.container {
  padding: 16px;
  
}
.mandatory{color:#660000;}

</style>