<template>
  <tr>
    <td>
      <span
          :class="{'finished': task.status === 'finished'}"
      >{{ task.title }}</span>
    </td>
    <td @click="this.$emit('change', task)" class="task__status">
      <span :class="getTodoClassNames">{{ task.status }}</span>
    </td>
    <td>
      <div @click="this.$emit('edit', task)" class="task__icon">
        <span class="fa fa-pen"></span>
      </div>
    </td>
    <td>
      <div @click="this.$emit('delete', task)" class="task__icon">
        <span class="fa fa-trash"></span>
      </div>
    </td>
  </tr>
</template>

<script>
export default {
  props: {
    task: Object
  },

  computed: {
    getTodoClassNames() {
      const allowedClass = {
        "to-do": "todo",
        "in-progress": "in-progress",
        "finished": "finished-status"
      }

      return allowedClass[this.task.status]
    }
  },
}
</script>

<style scoped>

</style>
