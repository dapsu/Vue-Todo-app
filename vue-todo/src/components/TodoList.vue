<template>
  <div>
    <transition-group name="list" tag="ul">
      <li v-for="(todoItem, index) in this.todoItems" v-bind:key="todoItem.item" class="shadow">
        <span @click="toggleComplete(todoItem, index)">
          <i class="fas fa-check checkBtn" v-bind:class="{checkBtnCompleted: todoItem.completed}"></i>
        </span>
        <span v-bind:class="{textCompleted: todoItem.completed}">
          {{ todoItem.item }}
        </span>
        <span @click="removeTodo(todoItem, index)" class="removeBtn">
          <i class="fas fa-trash-alt"></i>
        </span>
      </li>
    </transition-group>
  </div>
</template>

<script>
  import { mapGetters } from 'vuex';
  
export default {
  methods: {
    removeTodo: function(todoItem, index) {
      this.$store.commit('removeOneItem', { todoItem, index });
    },
    toggleComplete: function(todoItem, index) {
      this.$store.commit('toggleOneItem', { todoItem, index });
    }
  },
  computed: {   // 템플릿 내에서 연산이 이루어지지 않도록 computed 속성 이용
    // todoItems() {
    //   return this.$store.getters.storedTodoItems;
    // }
    ...mapGetters({ todoItems: 'storedTodoItems'}),
  }
}
</script>

<style scoped>
  ul {
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align:left;
  }
  li {
    display: flex;
    min-height: 50px;
    height: 50 px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }
  .checkBtn {
    line-height: 45px;
    color: #62acde;
    margin-right: 1rem;
    margin-top: 1rem;
  }
  .checkBtnCompleted {
    color: #b3adad;
  }
  .textCompleted {
    text-decoration: line-through;
    color: #b3adad;
  }
  .removeBtn {
    margin-left: auto;
    color: #de4343;
  }

  /* 리스트 아이템 트랜지션 효과 */
  .list-enter-active, .list-leave-active {
    transition: all 0.6s;
  }
  .list-enter, .list-leave-to {
    opacity: 0;
    transform: translateY(10px);
  }
</style>