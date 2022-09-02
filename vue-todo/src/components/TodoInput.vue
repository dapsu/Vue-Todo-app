<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
      <i class="fa-solid fa-plus addBtn"></i>
    </span>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      newTodoItem:''
    }
  },
  methods: {
    addTodo: function() {
      let obj = {   // 텍스트값이 체크되었는지 여부 확인하는 객체
        completed: false,
        item: this.newTodoItem
      };
      console.log(this.newTodoItem);
      // 저장하는 로직
      localStorage.setItem(this.newTodoItem, JSON.stringify(obj));  // 로컬스토리지에 저장
      this.clearInput();
    },
    clearInput: function() {
      this.newTodoItem = '';  // 저장 이후 인풋창에 작성된 값 지우기
    }
  }
}
</script>

<style scoped>
  input:focus {
    outline: none;
  }
  .inputBox {
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
  }
  .inputBox input {
    border-style: none;
    font-size: 1.4rem;
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