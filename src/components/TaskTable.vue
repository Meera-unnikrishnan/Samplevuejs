<template>
  <table border="3">
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
          <DeleteButton @delete="deleteTask(index)" />
        </td>
        <td>
          <EditButton @edit="editTask(index)" :task="task.task" />
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import DeleteButton from "./DeleteButton";
import EditButton from "./EditButton";

export default {
  props: {
    tasks: Array,
  },
  components: {
    DeleteButton,
    EditButton,
  },
  methods: {
    deleteTask(index) {
      this.$emit("delete", index);
    },
    editTask(index) {
      this.$emit("edit", index);
    },
  },
};
</script>

<style>
table {
  border-collapse: collapse;
  width: 100%;
  margin-top: 20px;
  border-width: thin;
  height: 60%;
}
</style>
