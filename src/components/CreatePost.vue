<template>
  <div>
    <from @submit.prevent="createPost">
      <div>
        <label for="userId">User ID</label>
        <input
          type="text"
          name="userId"
          id="userId"
          v-model="fromData.userId"
        />
      </div>

      <div>
        <label for="title">Post Title</label>
        <input type="text" name="title" id="title" v-model="fromData.title" />
      </div>

      <div>
        <label for="body">Post Body</label>
        <input type="text" name="body" id="body" v-model="fromData.body" />
      </div>

      <button type="submit">Create Post</button>
    </from>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "CreatePost",
  data() {
    return {
      fromData: {
        userId: "",
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      console.log("Creating post...");
      axios
        .post("https://jsonplaceholder.typicode.com/posts", this.fromData)
        .then((response) => console.log(response))
        .catch((error) => console.log(error));
    },
  },
};
</script>

<style scoped></style>
