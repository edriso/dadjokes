<template>
  <div class="single-joke">
    <nuxt-link to="/jokes">Back to jokes</nuxt-link>

    <h4 v-if="joke">{{ joke }}</h4>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      joke: ""
    };
  },

  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };

    try {
      const res = await axios.get(
        `https://icanhazdadjoke.com/j/${this.$route.params.id}`,
        config
      );
      this.joke = res.data.joke;
    } catch (error) {
      console.log(error);
    }
  },

  head() {
    return {
      title: this.joke,

      meta: [
        {
          hid: "description",
          name: "description",
          content: this.joke
        }
      ]
    };
  }
};
</script>

<style scoped>
.single-joke h4 {
  margin-top: 0.5rem;
  color: #444;
}
</style>
