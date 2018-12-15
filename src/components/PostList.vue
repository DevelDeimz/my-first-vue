<template>
  <div>
    <PostItem v-for="post in posts" :key="post.id" :post="post" @delete-post="deletePost(post)"/>
    <PostControl @add-post="addPost">Нужно заполнить все поля!</PostControl>
  </div>
</template>

<script>
import PostItem from "./PostItem.vue";
import PostControl from "./PostControl.vue";
import Vue from 'vue';

export default {
  data() {
    return {
      newPostId: 1,
      posts: null
    };
  },
  components: {
    PostItem, PostControl
  },
  methods: {
    deletePost: function(post) {
      if (this.posts.length === 1) {
        this.posts = null;
        return;
      }
      this.posts.splice(this.posts.indexOf(post), 1);
    },
    addPost: function(newPost) {
      if (!this.posts) {
        Vue.set(this, 'posts', []);
        this.newPostId = 1;
      }
      let post = {
        id: this.newPostId++,
        date: new Date().toLocaleString()
      };
      Object.assign(post, newPost);
      this.posts.push(post);
    }
  }
};
</script>