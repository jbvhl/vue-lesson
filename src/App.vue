<template>
  <div id="app">
    <h1>Panda Blogging</h1>
    <button @click='toggle'>Toggle</button>  
    <section v-if='showForm'>
      <h3>Add new blog post:</h3>
      <p>
        Author: <input type='text' v-model='author'/>
      </p>
      <p>
        <textarea name id cols='30' rows='10' v-model='post'></textarea>
        <br>
        <button @click='addPost'>Add Post</button>
      </p>
    </section>
    <section v-else>
      <h3>All posts:</h3>
      <post v-for='(postObj, i) in allPosts' :key='i' :postObj='postObj'/>
    </section>
  </div>
</template>

<script>
import Post from './components/Post';


export default {
  name: 'app',
  data: function () {
    return {
      showForm: true,
      author: '',
      post: '',
      allPosts: []
    }
  },
  methods: {
    toggle: function () {
      this.showForm = !this.showForm
    },
    
    addPost: function () {
      const newPost = {
        author: this.author,
        post: this.post
      };
      this.allPosts.push(newPost);
      this.author = '';
      this.post = '';
      this.toggle();
    }
  },

  components: {
    Post
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
