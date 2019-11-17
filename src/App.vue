<template>
  <div id="app">
      <h1>Alex Merced's Blog - Vue Front-End</h1>
      <div class="nav">
        <a href="http://www.alexmercedcoder.com">Portfolio</a>
        <a href="http://www.github.com/alexmercedcoder">Github</a>
        <a href="https://medium.com/@alexmercedcoder">Medium Articles</a>
        <a href="https://www.youtube.com/channel/UCoc4UCEetAt3htM3hV1dQgQ">Youtube</a>
      </div>
      <div class = "cards">
          <card v-for="post in posts" v-bind:post="post" :key="post.id"/>
      </div>
  </div>
</template>

<script>
import Card from '@/components/card.vue'

export default {
  name: 'app',
  components: {
      Card
  },

  data() {
      return {
        posts: [],
      }
    },

  methods:{
      async getPosts() {
  try {
    const response = await fetch('https://cdn.contentful.com/spaces/wiothdq64tqj/environments/master/entries?access_token=fbY3krPsiW8hWQ4m7GysjrfCfBdeCP9gBLqh3klbO20');
    const results = await response.json();
    await window.console.log(results);
    this.posts = results.items
    await window.console.log(this.posts);
  } catch (error) {
    window.console.log(error);
  }
    }
},

mounted() {
    this.getPosts();
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.nav {display: flex; justify-content: space-around; background-color: green; color: white; flex-wrap: wrap;}

.nav a {color: white; text-decoration: none; transition: color 2s, background-color 2s; padding: 5px; font-size: 1.5em;}

.nav a:hover {color: green; background-color: white;}

.cards {display: flex; flex-wrap: wrap; justify-content: space-around;}
</style>
