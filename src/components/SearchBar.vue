<template>
  <div>
    <input type="text" @input="onInput" />
  </div>
</template>



<script>
export default {
  name: "searchBar",
  methods: {
    onInput(e) {
      this.$emit("termChange", e.target.value);
    }
  }
};
</script>


<style scoped>
input {
  width: 80%;
}

div {
  text-align: center;
  margin: 20px;
}
</style>