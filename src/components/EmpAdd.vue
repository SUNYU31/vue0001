<template>
  <div>
    <form class="form-horizontal" role="form">
				<div class="form-group">
					<label for="firstname" class="col-sm-1 control-label">姓名</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="name" v-model="emp.name" placeholder="请输入姓名">
					</div>
				</div>
				<div class="form-group">
					<label for="lastname" class="col-sm-1 control-label">年龄</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="age" v-model="emp.age" placeholder="请输入年龄">
					</div>
				</div>
				<div class="form-group">
					<label for="lastname" class="col-sm-1 control-label">性别</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="sex" v-model="emp.sex" placeholder="请输入性别">
					</div>
				</div>
				<div class="form-group">
					<div class="col-sm-10 col-sm-offset-1">
						<button type="button" class="btn btn-default" @click="addemp()">提交</button>
					</div>
				</div>
			</form>
  </div>
</template>

<script>
export default {
  name: 'EmpAdd',
  data () {
    return {
       emp:{
      	name:'',
      	age:0,
      	sex:''
      }
    }
  },
  methods:{
  	 addemp:function(){
  	 	this.$http.post("http://localhost:8081/emp",{
  	 		name:this.emp.name,
  		  age:this.emp.age,
  		  sex:this.emp.sex
  	 	}).then(
  	 		function(res){
  	 			this.emp={
		      	name:'',
		      	age:'',
		      	sex:''
		      }
  	 			alert("录入成功！");
  	 			console.log(res);
  	 		},
  	 		function(error){
  	 			console.log(error);
  	 		}
  	 	)
  		
  	}
  }
}
</script>
 
<style scoped>
</style>
