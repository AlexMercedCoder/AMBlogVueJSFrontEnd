<template>
  <div id="card">
      <h1>{{post.fields.blogTitle}}</h1>
      <p>{{post.fields.blogContent}}</p>

  </div>
</template>

<script>


export default {
  name: 'card',
  components: {
  },
  props: {
      post: Object
  },
  mounted() {
      window.console.log(this.post);
    },
}
</script>

<style>
#card {display: flex; flex-direction: column; width: 300px; border-top: 5px groove green; padding: 4px; margin: 5px;}
</style>
