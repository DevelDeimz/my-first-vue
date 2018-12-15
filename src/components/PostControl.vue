<template>
  <div>
    <input type="text" v-model="newPost.title" required placeholder="Title">
    <br>
    <textarea v-model="newPost.text" required placeholder="Post text"></textarea>
    <br>
    <slot v-if="!isValid"></slot>
    <button @click="clearForm">clear form</button>
    <label @click="toggle = !toggle">
      <button @click="$emit('add-post', newPost)" v-if="isValid">add post</button>
    </label>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      newPost: {
        title: "",
        text: "",
        isEdit: false
      },
      toggle: true
    };
  },
  computed: {
    isValid: function() {
      return this.newPost.title && this.newPost.text;
    }
  },
  methods: {
    clearForm: function() {
      this.newPost.title = "";
      this.newPost.text = "";
    }
  },
  watch: {
    toggle: function() {
      this.clearForm();
    }
  }
};
</script>