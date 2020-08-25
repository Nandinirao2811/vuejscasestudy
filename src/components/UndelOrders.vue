<template>
<div class="UndelOrders">
<h1> {{msg}} </h1>
<form class="container">
   <div >
   <table id="undel">
   <thead>
   <tr>
            <th> Order Id</th>
             <th> Recipient Name </th>
            <th> Gift Card Value (Total) </th>
            <th> Undelivered Status </th>            
   </tr>
   </thead>
   <tbody v-for="undelOrd in neworder" :key="undelOrd.id">
   <tr>
        <td> {{undelOrd.id}} </td>
          <td> {{undelOrd.recFN}} {{undelOrd.recLN}} </td>
              <td> INR {{undelOrd.amtPay}} </td>
                <td> {{undelOrd.sts}} </td>
              
   </tr>
   </tbody>
   
   </table>
      <button type="button" v-on:click="previous()"> Previous </button>  
<br>
        </div>
        
        </form>

</div>

</template>
<script>

export default {
    name:'UndeliveredOrders',
    data: function(){
       return{
           msg:'Bloom Gift Cards - List of UnDelivered Orders',
           neworder:[]
       }
    },
    methods:{
        GetUndelOrders: function(){
            this.$http.get('http://localhost:3000/neworder')
            .then(res=> {
                console.log(res.data)
                this.neworder = res.data
            }, err=> {
                console.log(err)
            })
        },
         previous:function(){
          this.$router.push({path:'/adminprofile'})
          console.log("previous page")
      }
    },
    
    created:function(){
    this.GetUndelOrders()
  }
}

</script>
<style scoped>
#undel {

  border-collapse: collapse;
  width: 100%;
}

#undel td, #undel th {
  border: 1px solid #ddd;
  padding: 8px;
}

#undel tr:nth-child(even){background-color: #f2f2f2;}

#undel tr:hover {background-color: #ddd;}

#undel th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: center;
  background-color: #336699;
  color: white;
}
.container {
  padding: 16px;
  
}
button {
  background-color:#264d73;
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
</style>