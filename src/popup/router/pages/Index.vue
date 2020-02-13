<template>
  <div style="width: 600px; height: 510px">
    <p>Hello world!!!</p>
    <v-banner two-line>
      <v-avatar
              slot="icon"
              color="deep-purple accent-4"
              size="40"
      >
        <v-icon
                icon="mdi-lock"
                color="white"
        >
          mdi-lock
        </v-icon>
      </v-avatar>

      Three line text string example with two actions. One to two lines is preferable. Three lines should be considered the maximum string length on desktop in order to keep messages short and actionable.

      <template v-slot:actions>
        <v-btn text color="deep-purple accent-4">Action</v-btn>
        <v-btn text color="deep-purple accent-4">Action</v-btn>
      </template>
    </v-banner>
    <div v-for="post in posts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [],
    };
  },
  async mounted() {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts?_limit=3');
    const posts = await res.json();
    this.posts = posts;
  },
};
</script>

<style lang="scss" scoped>
p {
  font-size: 20px;
}
</style>
