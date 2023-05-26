<template>
  <button class="delbtn" @click="handleDelete">Delete</button>
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
.delbtn {
  border: none;
  background-color: red;
  color: white;
  height: 25%;
  width: 50%;
  border-radius: 20px;
  font-size: 20px;
  margin: 30px;
}
</style>
