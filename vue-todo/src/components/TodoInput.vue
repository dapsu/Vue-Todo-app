<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
      <i class="fa-solid fa-plus addBtn"></i>
    </span>

    <Modal v-if="showModal" @close="showModal=false">
      <h3 slot="header">
        경고!
        <span @click="showModal=false" @keyup.enter="showModal=false">
          <i class="fas fa fa-times closeModalBtn"></i>
        </span>
      </h3>
      <span slot="body">아무것도 입력하지 않았습니다.</span>
    </Modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue'
export default {
  data: function() {
    return {
      newTodoItem:'',
      showModal: false,
    }
  },
  methods: {
    addTodo: function() {
      if (this.newTodoItem !== '') {
        this.$emit('addTodoItem', this.newTodoItem);
        this.clearInput();
      } else {
        this.showModal = !this.showModal;
      }
    },
    clearInput: function() {
      this.newTodoItem = '';  // 저장 이후 인풋창에 작성된 값 지우기
    }
  },
  components: {
    Modal: Modal,
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
  .closeModalBtn {
    color: #42b983;
  }
</style>