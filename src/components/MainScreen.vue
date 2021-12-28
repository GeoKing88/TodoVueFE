<template>
  <div>
    <b-container>
      <b-row>
        <b-col cols="2">
          <p>Categorias</p>
        </b-col>
        <b-col cols="10">
          <Todo :results="results"></Todo>
          <Category></Category>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Todo from "@/components/Todo";
import Category from "@/components/Category"

export default {
  name: "MainScreen",
  data() {
    return {
      results: [],
    };
  },
  components: {
    Todo,
    Category
  },

  async mounted() {
    await this.fetchTodos();
    console.log(this.results);
  },
  methods: {
    async fetchTodos() {
      this.results = [];
      await fetch("http://localhost:8080/api/v1/todo/getalltodos")
          .then((response) => response.json())
          .then((data) => data.forEach((el) => this.results.push(el)));
    },
  },
};
</script>
