<template>
  <div>
    <button @click="getPosts">Load Posts</button>
    <div v-if="loading">
      <h4>Loading data.....</h4>
    </div>
    <div v-if="errorMsg">
      <h2>{{ errorMsg }}</h2>
    </div>
    <div v-for="post in posts" :key="post.id">
      <h3>{{ post.id }}. {{ post.title }}</h3>
      <p>{{ post.body }}</p>
      <hr />
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "PostList",
  data() {
    return {
      posts: [],
      errorMsg: "",
      loading: false,
    };
  },
  methods: {
    getPosts() {
      this.loading = true;
      axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then((response) => {
          this.posts = response.data;
        })
        .catch((error) => {
          console.log(error);
          this.errorMsg = "Error in retriving Posts!";
        });
      this.loading = false;
    },
  },
};
</script>

<style>
button {
  padding: 5px 12px;
  font-size: 25px;
  border-radius: 7px;
  border: none;
  outline: none;
  cursor: pointer;
  margin: 10px 3px;
}
button:hover {
  background-color: azure;
  border: 2px solid aquamarine;
}
</style>
