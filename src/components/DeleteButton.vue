<template>
  <!-- <button class="delbtn" @click="handleDelete">Delete</button> -->
 <div>
 
   <v-btn class="ml-5" color="error" @click="handleDelete">
    <v-icon left>
            mdi-delete
        </v-icon>
        Delete
        </v-btn>
   </div>
</template>

<script>

export default {
  methods: {
    handleDelete() {
      this.$emit("delete");
    },
  },
};
</script>
<style>
/* .delbtn {
  border: none;
  background-color: red;
  color: white;
  height: 25%;
  width: 50%;
  border-radius: 20px;
  font-size: 20px;
  margin: 30px;
} */
</style>
