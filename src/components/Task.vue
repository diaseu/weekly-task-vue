<template>
  <div 
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>
      {{ task.text }}
      <i @click="onDelete()" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: {
    task: Object
  },
  method: {
    onDelete(id) {
      this.$emit('delete-task', id)
    }
  }
}
</script>

<style scoped>
.fas {
  color: #F587C1;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 15px;
}
.task.reminder {
  border-left: 5px solid #F587C1;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>