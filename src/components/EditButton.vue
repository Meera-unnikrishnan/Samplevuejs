<template>
  <!-- <button class="editbtn" @click="handleEdit">Edit</button> -->
  <v-btn class="ml-5" color="success" @click="handleEdit">
     <v-icon left>
            mdi-pencil
        </v-icon>
        Edit
  </v-btn>
  
</template>

<script>
export default {
  methods: {
    handleEdit() {
      this.$emit("edit");
    },
  },
};
</script>
<style>
/* .editbtn {
  border: none;
  background-color: #77b631;
  color: white;
  height: 25%;
  width: 50%;
  border-radius: 20px;
  font-size: 20px;
  margin: 30px;
} */
</style>
