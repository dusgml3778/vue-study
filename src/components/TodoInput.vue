<template>
  <div class="inputBox shadow">
    <!-- v-model 역할 input에 입력된 텍스트 값을 동적으로 vue 인스턴스 안에 매핑-->
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
    <span class = "addContainer">
    <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>
  </div>
</template>

<script>
export default {
  data:function(){
    return {
      newTodoItem : ""
    }
  },
  methods:{
    addTodo:function(){
      if(this.newTodoItem !== ""){
      //this.$emit("이벤트 이름", 인자) ->상위컴포넌트에 보낼 이벤트 랑 인자
      this.$emit("addTodoItem", this.newTodoItem)
      this.clearInput();
      }
    },
    clearInput :function(){
      this.newTodoItem = "";
    }

  }
}
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: rgb(221, 221, 218);
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>