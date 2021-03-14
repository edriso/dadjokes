<template>
  <form class="search" @submit.prevent="onSubmit">
    <input type="text" v-model="text" placeholder="Search Jokes ..." />

    <input type="submit" value="Seach Jokes" />
  </form>
</template>

<script>
export default {
  data() {
    return {
      text: ""
    };
  },

  methods: {
    onSubmit() {
      this.$emit("searching", this.text);
      // this.text = "";
    }
  }
};
</script>

<style scoped>
/* .search form {

} */

.search input:focus {
  outline: none;
}

.search input[type="text"]::placeholder {
  color: #fff;
  opacity: 1;
}

.search input[type="text"] {
  background-color: #9e8f8f;
  color: #fff;
  border: none;
  padding: 0.5rem;
  border-radius: 0.25rem;
}

.search input[type="submit"] {
  cursor: pointer;
  padding: 0.5rem;
  border: none;
  background-color: #9e8f8f;
  color: #fff;
  border-radius: 0.25rem;
}
</style>
