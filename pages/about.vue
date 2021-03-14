<template>
  <div class="about">
    <h2>About Dadjokes</h2>
    <p>
      the dad jokes that you need wherever you are.
    </p>
    <a
      href="https://icanhazdadjoke.com/"
      target="_blank"
      rel="noopener noreferrer"
      >API link</a
    >
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "About The App",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Best place for dad jokes"
        }
      ]
    };
  }
};
</script>

<style scoped>
.about h2 {
  margin-bottom: 0.5rem;
}
</style>
