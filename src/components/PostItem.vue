<template>
  <div>
    <div v-if="!post.isEdit">
      <h1>{{post.title}}</h1>
      <p>{{post.text}}</p>
    </div>
    <div v-else>
      <input type="text" v-model="post.title" placeholder="Title">
      <br>
      <textarea type="text" v-model="post.text" placeholder="Post text"></textarea>
      <br>
    </div>
    <div>
      <small>{{post.date}}</small>
      <button @click="$emit('delete-post')">delete post</button>
      <button @click="post.isEdit = !post.isEdit">edit post</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      default: {}
    }
  }
};
</script>