<template>
  <div class="todo__action">
    <input
        class="input default-border"
        :value="modelValue"
        @keyup="$emit('update:modelValue', $event.target.value)"
        type="text"
        placeholder="Enter task"
    >
    <button @click="addTask" class="btn">SUBMIT</button>
  </div>
</template>

<script>
export default {
  props: {
    modelValue: String
  },

  methods: {
    isValid() {
      return this.modelValue.length !== 0
    },

    addTask() {
      if (this.isValid()) {
        this.$emit("create", {
          id: Date.now(),
          status: "to-do",
          title: this.modelValue
        });

        this.$emit('update:modelValue', '')
      }
    }
  }
}
</script>

<style scoped>

</style>
