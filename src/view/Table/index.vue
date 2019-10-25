<style scoped>
	
</style>
<template>
	  <div>
        <mydiv v-bind:info="info" v-bind:header="header" v-bind:num="num" v-bind:page="page"  ></mydiv> 
    </div>
</template>
<script>
     import mydiv from '@/components/myDiv';
	 export default{
     components:{
      mydiv
     },
	 	 data(){
	 	 	return{
           boolen:true,
            num:5,
           page:1,
           info:[],
           header:[{
            key: '名称',
            name:'name'
             }, {
            key: '价格',
            name:'price'
             }, {
            key: '数量',
            name:'num'
             }]
	 	 	}
	 	 },
     mounted(){
       
         for(var i = 0;i<22;i++){
    this.info.push({
     name:'手机'+i,
     num:i,
     price:100*i
     })
   }

       }
     }
     

</script>