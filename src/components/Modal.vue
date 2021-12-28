<template>
  <div>
    <b-modal id="modal-1" title="Todo">
      <b-form>
          <b-form-group
              id="input-group-1"
              label="Todo Email:"
              label-for="input-1"

          >
            <b-form-input
                id="input-1"
                v-model="todoResult.name"
                type="email"
                placeholder="Todo Name"
                required>

            </b-form-input>
        </b-form-group>
      </b-form>

    </b-modal>
  </div>
</template>

<script>

export default {
  name: 'Modal',
  props: {
    todoResult: {
      type: Object,
      default: () => {}
    }
  },
  data() {
    return {
      cloneResult: {... this.todoResult},
      isCompleted: [],
      options: [
        {item: true},
        {item: false}
      ]
    }
  },
  methods: {
  },

}
</script>

<style scoped>

</style>