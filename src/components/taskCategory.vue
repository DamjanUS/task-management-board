<template>
   <div class="tasks">
    <div class="fontSizeT">{{category.name}}</div>
    <all-tasks v-for="task in category.tasks" :key="task.id" :task="task"> </all-tasks>  
  </div>
</template>

<script>
import allTasks from "@/components/allTasks.vue"
export default {

  props: {
      category: Object
    },
    components: {
      allTasks
    }
}
</script>

<style lang="postcss" scoped>
.tasks {
  @apply border border-stone-300 rounded-xl p-3 m-2 w-56 bg-blue-600;
}
.fontSizeT {
  @apply text-xl;
}
</style>