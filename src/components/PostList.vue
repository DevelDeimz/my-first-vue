<template>
  <div>
    <PostItem v-for="post in posts" :key="post.id" :post="post" @delete-post="deletePost(post)"/>
    <PostControl @add-post="addPost">Нужно заполнить все поля!</PostControl>
  </div>
</template>

<script>
import PostItem from "./PostItem.vue";
import PostControl from "./PostControl.vue";

export default {
  data() {
    return {
      newPostId: 1,
      posts: []
    };
  },
  components: {
    PostItem, PostControl
  },
  methods: {
    deletePost: function(post) {
      this.posts.splice(this.posts.indexOf(post), 1);
    },
    addPost: function(newPost) {
      if (this.posts.length === 0) {
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