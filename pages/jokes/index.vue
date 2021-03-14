<template>
  <div class="jokes">
    <SearchJokes @searching="filterJokes" />
    <Joke v-for="jokeObj in jokes" :key="jokeObj.id" :jokeObj="jokeObj" />
  </div>
</template>

<script>
import Joke from "@/components/Joke.vue";
import SearchJokes from "@/components/SearchJokes.vue";
import axios from "axios";

export default {
  components: { Joke, SearchJokes },

  data() {
    return {
      jokes: []
    };
  },

  methods: {
    async filterJokes(txt) {
      // this.jokes = this.jokes.filter(jokeObj => {
      //   return jokeObj.joke.toLowerCase().match(txt.toLowerCase());
      // });

      const config = {
        headers: {
          Accept: "application/json"
        }
      };

      try {
        const res = await axios.get(
          `https://icanhazdadjoke.com/search?term=${txt}`,
          config
        );
        this.jokes = res.data.results;
      } catch (error) {
        console.log(error);
      }
    }
  },

  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };

    try {
      const res = await axios.get("https://icanhazdadjoke.com/search", config);
      this.jokes = res.data.results;
    } catch (error) {
      console.log(error);
    }
  },

  head() {
    return {
      title: "Jokes",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Dad jokes"
        }
      ]
    };
  }
};
</script>
