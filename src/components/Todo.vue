<template>
  <div>
    <!--b-button @click="showModal">{{ result.name }}</b-button> -->
    <ul>
      <li v-for="todo in results" :key="todo.id">
        <b-button v-b-modal.modal-1 @click="selectTodo(todo)"> {{todo.name}} </b-button>
      </li>
    </ul>
    <Modal :todoResult="selectedTodo" v-if="selectedTodo"></Modal>
  </div>
</template>

<script>

import Modal from "@/components/Modal.vue"

export default {
  name: 'Todo',
  data() {
    return {
      isModalVisible: false,
      selectedTodo: undefined
    }
  },
  components: {Modal},
  props: {
    results: {
      type: Array
    }
  },

  methods: {
    showModal() {
      console.log(this.result.name)
      this.resultToShow = undefined
      this.resultToShow = this.result
      this.$emit("bv::show::modal", "modal")
      this.isModalVisible = true
    },
    selectTodo(todo){
      console.log(todo.name)
      this.selectedTodo = todo
    }
  }
}
</script>