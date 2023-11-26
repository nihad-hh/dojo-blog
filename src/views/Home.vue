<template>
  <div class="home">
    <h1>Home</h1>
    <PostList :posts="posts" />
    <button @click="showPosts = !showPosts">toggle posts</button>
  </div>
</template>

<script>
import PostList from "../components/PostList.vue";
import getPosts from "../composables/getPosts";

export default {
  name: "Home",
  components: { PostList },
  setup() {
    const { posts, error, load } = getPosts();

    load();

    return { posts, error };
  },
  created() {},
  mounted() {},
};
</script>
