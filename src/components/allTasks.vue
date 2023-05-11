<template>
<div class="tasks">
  <div class="fontSizeT">{{ task.title }}</div>
  <div>{{ task.description }}</div>
  <div>Due Date:{{ formatDate }}</div>
  <div v-if="dueTime < 0">Task overdue {{dueTime*(-1)}} days</div>
  <div v-else >Due in {{ dueTime }} days</div>
  <CheckBox label="Completed" :value="task.completed" @input="task.completed = $event"></CheckBox> 
</div> 
</template>

<script>
import CheckBox from '@/components/CheckBox.vue'
import { format } from 'date-fns'
import { differenceInDays } from 'date-fns'

export default {
  data() {
    return{
    currentDate: new Date(), 
    isDivVisible: true
    }
  },
    props:{
      task: Object  
    },
     methods:{
    
  },
  computed:{
formatDate(){
       const formatD = format(this.task.dueDate,'dd MMM yyyy HH:mm')
       return formatD
    },
dueTime(){  
     const result = differenceInDays(
      this.task.dueDate,this.currentDate
     )
     return result   
},

  },
    components:{
      CheckBox  
    }
}
</script>

<style lang="postcss" scoped>
.tasks{
    @apply border border-stone-300 rounded-xl p-3 m-2 w-56 bg-blue-300; 
}
.fontSizeT{
  @apply text-xl
}
</style>

 