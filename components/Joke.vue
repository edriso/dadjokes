<template>
  <div class="joke">
    <!-- <nuxt-link :to="`/jokes/${jokeObj.id}`">{{ jokeObj.joke }}</nuxt-link> -->
    <nuxt-link :to="{ name: 'jokes-id', params: { id: jokeObj.id } }">
      <p>
        {{ jokeObj.joke }}
      </p>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  name: "Joke",

  props: ["jokeObj"]
};
</script>

<style>
.joke {
  padding: 1rem;
  border: 1px dotted #ccc;
  margin: 1rem 0;
}
</style>
