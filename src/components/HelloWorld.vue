<template>
  <div class="hello">
    <draggable v-model="tasks">
      <!-- <allTasks
      v-for="task in sortTask"
      :key="task.id"
      :task="task"
      @completed="
        (event) => {
          task.completed = event;
        }
      "
    ></allTasks> -->
      <taskCategory
        v-for="category in taskCategories"
        :key="category.id"
        :category="category"
      >
      </taskCategory>
      <!-- <all-tasks v-for="task in tasks" :key="task.id" > </all-tasks>   -->
    </draggable>
  </div>
</template>

<script>
// import AllTasks from "./allTasks.vue";
import draggable from "vuedraggable";
import taskCategory from "./taskCategory.vue";
import _ from "lodash";

//import PButton from '@/components/PButton.vue'
//import Checkbox from '@/components/CheckBox.vue'

export default {
  data() {
    return {
      available: true,
      tasks: [
        {
          id: 1,
          title: "Monday",
          description: "workday1",
          completed: false,
          dueDate: new Date(2022, 5, 17, 14, 30),
        },
        {
          id: 2,
          title: "Tuesday",
          description: "workday2",
          completed: false,
          dueDate: new Date(2024, 3, 21, 16, 15),
        },
        {
          id: 3,
          title: "Wednesday",
          description: "workday3",
          completed: false,
          dueDate: new Date(2023, 4, 11, 12, 50),
        },
        {
          id: 4,
          title: "Thursday",
          description: "workday4",
          completed: false,
          dueDate: new Date(2022, 7, 7, 11, 35),
        },
        {
          id: 5,
          title: "Friday",
          description: "workday5",
          completed: false,
          dueDate: new Date(2024, 11, 29, 9, 45),
        },
      ],
      taskCategories: [
        {
          id: 1,
          name: "categoryOne",
          tasks: [
            {
              id: 1,
              title: "January",
              description: "workmonth1",
              completed: false,
              dueDate: new Date(2024, 12, 21, 7, 15),
            },
          ],
        },
        {
          id: 2,
          name: "categoryTwo",
          tasks: [
            {
              id: 2,
              title: "February",
              description: "workmonth2",
              completed: false,
              dueDate: new Date(2024, 9, 17, 11, 25),
            },
          ],
        },
        {
          id: 3,
          name: "categoryThree",
          tasks: [
            {
              id: 3,
              title: "April",
              description: "workmonth3",
              completed: false,
              dueDate: new Date(2025, 8, 19, 19, 55),
            },
          ],
        },
      ],
    };
  },
  name: "HelloWorld",
  props: {
    msg: String,
  },
  methods: {
    isCompleted(e) {
      console.warn(e);
    },
  },
  computed: {
    sortTask() {
      return _.sortBy(this.tasks, "completed");
    },
  },
  components: {
    // AllTasks,
    draggable,
    taskCategory,
    /*  PButton,
    Checkbox */
  },
};
</script>


<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
