<template>
  <div>
    <v-col cols="12" sm="6">
      <v-text-field
        v-model="inputTask"
        label="Insert a new task"
        outlined
        clearable
        @keyup.enter="handleNewTask"
      ></v-text-field>
    </v-col>
    <v-list flat subheader>
      <v-list-item-group multiple active-class="">
        <v-row v-for="(task, index) in tasksList" :key="index">
          <task-component :task="task" />
        </v-row>
      </v-list-item-group>
    </v-list>
  </div>
</template>

<script>
import TaskComponent from "@/components/tasks/TaskComponent.vue";

export default {
  name: "TaskPage",
  components: {
    TaskComponent,
  },
  data() {
    return {
      inputTask: null,
      tasksList: [
        { title: "Ir ao mercado", concluded: " false" },
        { title: "Comprar ração", concluded: " false" },
        { title: "Ver TV", concluded: " false" },
      ],
    };
  },
  methods: {
    handleNewTask() {
      if (this.inputTask) {
        this.tasksList.push({
          title: this.inputTask,
          concluded: false,
        });
        this.inputTask = null;
      }
    },
  },
};
</script>
