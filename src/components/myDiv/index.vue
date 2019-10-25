<template>

   <div>
    <table>
     <tr>
      <th v-for='x in header' v-on:click="bit(x)">{{x.key}}</th>
     </tr>
     <tr v-for="y in fenye">
      <th v-for="x in header">{{y[x.name]}}</th>
     </tr>
    </table>
    <button v-on:click="lastPage">上一页</button>   
    <button v-on:click="nextPage">下一页</button>  
   </div>

</template>
<script type="text/javascript">
	export default{
		  props:{
		  	 info:Array,
             header:Array,
             num:Number,
             page:Number,
             boolen:Boolean,
             tiaojian:String
		  },
		  data(){
		  	return{

		  	}
		  },
		  computed:{
		  	   fenye:function(){
      /*排序*/
      var list=this.info;
      var paixu=this.tiaojian;
       for(var i = 1;i<list.length;i++){
        for(var j=0;j<list.length-i;j++){
         if(this.boolen){
          if(list[j][paixu]>list[j+1][paixu]){
           var k=list[j+1];
           list[j+1]=list[j];
           list[j]=k;
          }
         }else{
          if(list[j][paixu] < list[j + 1][paixu]) {
           var k;
           k = list[j];
           list[j] = list[j + 1];
           list[j + 1] = k;
          }
         }
        }
       }
      /*分页*/
      var list2 = [];
      var start= this.num*(this.page-1);
      var end=start+this.num;
      if(end<list.length){
       for(var i =start;i<end;i++){
        list2.push(list[i])
       }
      }else{
       for(var i =start;i<list.length;i++){
        list2.push(list[i])
       }
      }
      return list2;
     }
		  },
		  methods:{
		  	  bit:function(x){
      this.boolen=!this.boolen;
      this.tiaojian=x.name;      
     },
     lastPage:function(){
      console.log(this.num)
      if(this.page > 1) {
       this.page = this.page - 1;
      }
     },
     nextPage: function() {
      var pageNum = this.info.length / this.num;
      if(this.page < pageNum) {
       this.page = this.page + 1;
      }
     }
		  }
	}
</script>