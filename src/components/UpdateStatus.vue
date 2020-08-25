<template>
<div class="UpdateStatus">
<h1> {{msg}} </h1>
<form class="container">
   <div >
   
   <!-- <v-bind:stsupd="status" > -->
   <table id="sts">
   <thead>
   <tr>
            <th> Order Id</th>
             <th> Recipient Name </th>
             <th> Ordered Date </th>
             <th> Gift Card Value (Rs) </th>
             <th> Commission Amount (5%) </th> 
             <th> Amount Payable </th>
             <th> Delivery Status </th>
             <th> Update Status </th>
             <th> Status </th>
             
   </tr>
   </thead>
   <tbody v-for="sts in neworder" :key="sts.id">
   <tr>
        <td> {{sts.id}} </td>
          <td> {{sts.recFN}} {{sts.recLN}} </td>
            <td> {{sts.date}} </td>
              <td> INR {{sts.gcv}} </td>
                <td> INR {{sts.comAmt}} </td>
                <td> INR {{ sts.amtPay}} </td>
                <td> {{sts.sts}}  </td>
                <td>
                
                <div v-on:del="updatests($event)" v-bind:status="updsts" >
                  <button type="button" v-on:click="del()"> Status </button>
                  </div>
                   </td>    
                             <td> {{updsts}} </td>       
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
    name:'updatestatus',
      props: {
           status: String
         },
         
    data: function(){
       return{
           msg:'----- Bloom Gift Cards - Update Status Here -----',   
         //  status:"fdd", 
          updsts:"Updation InProgress",
           neworder:[]
       }
    },
    methods:{    
        GetUpdateSts: function(){
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
        },
        del:function(){ 
            this.$emit("del","Delivered")
             console.log("Status Updated to Delivered")
        },
        updatests(data){
        this.status = data
      }
        // updateSts:function(){       
        //   if(this.neworder[0].id == null){
        //      this.neworder.sts ="Delivered"
        //      this.neworder.push("Status Updated")
        //   return this.neworder.sts
        //   }     
        // }
    },
    
    created:function(){
    this.GetUpdateSts()
 //   console.log("get")
  //this.updateSts()
  // console.log("put")
  }
}
</script>
<style scoped>
#sts {

  border-collapse: collapse;
  width: 100%;
}

#sts td, #sts th {
  border: 1px solid #ddd;
  padding: 8px;
}

#sts tr:nth-child(even){background-color: #f2f2f2;}

#sts tr:hover {background-color: #ddd;}

#sts th {
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
  text-align:center;
  cursor: pointer;
  width: 18%;
  opacity: 0.9;

  
}
button:hover {
  opacity:1;
}
</style>