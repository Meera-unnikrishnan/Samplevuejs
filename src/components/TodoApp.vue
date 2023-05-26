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
    <table border="{3}">
      <thead>
        <tr>
          <th>Task</th>
          <th>Delete</th>
          <th>Edit</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
        
          <td align="center">{{ task.task }}</td>

          <td>
            <button class="delbtn" @click="deleteTask(index)">Delete</button>
          </td>
          <td>
            <button class="editbtn" @click="EditTask(index)">Edit</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "TodoApp",
  props: {
    msg: String,
  },
  data() {
    return {
      task: "",
      editTask: null,
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

    EditTask(index) {
      (this.task = this.tasks[index].task), (this.editTask = index);
    },

    SubmitTask() {
      if (this.task.length === 0) {
        return;
      }
      if (this.editTask != null) {
        this.tasks[this.editTask].task = this.task;
        this.editTask = null;
      } else {
        this.tasks.push({
          task: this.task,
        });
      }
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
table {
  border-collapse: collapse;
  width: 100%;
  margin-top: 20px;
  border-width: thin;
  height: 60%;
}

.btn {
  border: none;
  width: 80px;
  height: 40px;
  padding: 2px;
  background-color: black;
  color: white;
  border-radius:10px;
}

.delbtn {
  border: none;
  background-color: red;
  color: white;
  height:25%;
  width:50%;
  border-radius:20px;
  font-size:20px;
  margin:30px;
}

.editbtn {
  border: none;
  background-color: #77b631;
  color: white;
  height:25%;
  width:50%;
  border-radius:20px;
  font-size:20px;
   margin:30px;
}

</style>
