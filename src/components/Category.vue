<template>
  <div>
    <ul>
      <li v-for="category in categories" :key="category.id">
        {{ category.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Category",
  data() {
    return {
      categories: []
    }
  },
  methods: {
    async getAllCategories() {
      await fetch("http://localhost:8080/api/v1/category/getallcategories")
          .then((response) => response.json())
          .then((data) => data.forEach((el) => {
            //console.log(el.name)
            this.categories.push(el)
          }))
    }
  },
  async mounted() {
    await this.getAllCategories()
  }
}
</script>

<style scoped>

</style>