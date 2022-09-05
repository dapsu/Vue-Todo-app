<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>
    
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  data: function() {
    return {
      todoItems: [],
    }
  },
  components: {
    // 컴포넌트 태그명: 컴포넌트 내용 
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter,
  },
  methods: {
    // addOneItem: function(todoItem) {
    //   let obj = {   // 텍스트값이 체크되었는지 여부 확인하는 객체
    //     completed: false,
    //     item: todoItem
    //   };
    //   localStorage.setItem(todoItem, JSON.stringify(obj));  // 로컬스토리지에 저장
    //   this.todoItems.push(obj);
    // },
    // removeOneItem: function(todoItem, index) {
    //   localStorage.removeItem(todoItem.item);
    //   this.todoItems.splice(index, 1);
    // },
    // toggleOneItem: function(todoItem, index) {
    //   this.todoItems[index].completed = !this.todoItems[index].completed;
    //   // 로컬스토리지를 업데이트하는 api가 없기 때문에 삭제 후 다시 생성
    //   localStorage.removeItem(todoItem.item);
    //   localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    // },
    // clearAllItems: function() {
    //   localStorage.clear();
    //   this.todoItems = [];
    // }
  }
}
</script>

<style>
  body {
    text-align: center;
    background-color: rgb(198, 174, 220);
  }
  input {
    border-style: groove;
    width: 200px;
  }
  button {
    border-style: groove;
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
  }
</style>
