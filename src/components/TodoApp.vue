<template>
  <div class="container">
    <center>
      <h2 class="heading">Todo List</h2>
    </center>
    <center>
      <div>
        <input
          class="input-text"
          type="text"
          v-model="task"
          placeholder="New Task here.."
        />
        <button class="btn" @click="SubmitTask">ADD</button>
      </div>
    </center>
    <TaskTable :tasks="tasks" @delete="deleteTask" @edit="editTask" />
  </div>
</template>

<script>
import TaskTable from "./TaskTable.vue";

export default {
  name: "TodoApp",
  props: {
    msg: String,
  },
  components: {
    TaskTable,
  },
  data() {
    return {
      task: "",
      editTaskIndex: null,
      tasks: [
        {
          task: "Learning React js",
        },
        {
          task: "Learning Vue js",
        },
        {
          task: "Learning Node js",
        },
      ],
    };
  },
  methods: {
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    editTask(index) {
      this.task = this.tasks[index].task;
      this.editTaskIndex = index;
    },
    SubmitTask() {
      if (this.task.length === 0) {
        return;
      }
      if (this.editTaskIndex !== null) {
        this.tasks[this.editTaskIndex].task = this.task;
        this.editTaskIndex = null;
      } else {
        this.tasks.push({
          task: this.task,
        });
      }
      this.task = "";
    },
  },
};
</script>

<style>
.container {
  width: 900px;
  margin: auto;
  height: 100vh;
  font-size: 30px;
}

.input-text {
  border-radius: 10px;
  margin-right: 10px;
  height: 30px;
}

.btn {
  border: none;
  width: 80px;
  height: 40px;
  padding: 2px;
  background-color: black;
  color: white;
  border-radius: 10px;
}
</style>
