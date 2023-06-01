<template>
  <div class="container">
    <center>
      <h2 class="heading">Todo List</h2>
    </center>
    <center>
      <v-col cols="12" sm="6" md="6">
        <v-text-field
          placeholder="New Task Here"
          outlined
          v-model="task"
        ></v-text-field>
      </v-col>
      <!-- <input
          class="input-text"
          type="text"
          placeholder="New Task here.."
        /> -->

      <div>
        <v-btn x-large rounded color="success" dark @click="SubmitTask">
          <v-icon dark> mdi-plus </v-icon>
          ADD
        </v-btn>
      </div>
    </center>
    <TaskTable :tasks="tasks" @delete="confirmDelete" @edit="editTask" />
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
    confirmDelete(index) {
      const confirmation = confirm(
        "Are you sure you want to delete this task?"
      );
      if (confirmation) {
        this.deleteTask(index);
      }
    },
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
        const confirmation = confirm(
          "Are you sure you want to edit this task?"
        );
        if (confirmation) {
          this.tasks[this.editTaskIndex].task = this.task;
          this.editTaskIndex = null;
        }
      } else {
        const confirmation = confirm("Are you sure you want to add this task?");
        if (confirmation) {
          this.tasks.push({
            task: this.task,
          });
        }
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

/* .input-text {
  border-radius: 10px;
  margin-right: 10px;
  height: 30px;
} */

/* .btn {
  border: none;
  width: 80px;
  height: 40px;
  padding: 2px;
  background-color: black;
  color: white;
  border-radius: 10px;
} */
</style>
