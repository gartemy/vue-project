<template>
  <div id="app">
    <post-form
      @add="addPost"
    ></post-form>

    <div class="posts">
      <h2>Список постов</h2>

      <post-list
        :posts="posts"
      ></post-list>
    </div>
  </div>
</template>

<script>
import PostList from '@/components/PostList.vue'
import PostForm from '@/components/PostForm.vue'

export default {
  name: 'App',
  components: {
    PostList, PostForm,
  },
  data() {
    return {
      title: '',
      text: '',
      posts: [
        {
          id: 1,
          title: 'Пост №1',
          body: 'Текст поста №1',
        },
        {
          id: 2,
          title: 'Пост №2',
          body: 'Текст поста №2',
        },
      ],
    };
  },
  methods: {
    addLike() {
      this.likes += 1
    },
    addDislike() {
      this.dislikes += 1
    },
    addPost(post) {
      this.posts.push(post);
    },
    deletePost(index) {
      this.posts.splice(index, 1);
    }
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 60px 20px 0 20px;
}

.like {
  background: green;
  color: white;
  cursor: pointer;
}

.dislike {
  background: red;
  color: white;
  cursor: pointer;
}

.form {
  margin-bottom: 30px;
}

h1 {
  margin-bottom: 10px;
}

h2 {
  margin-bottom: 10px;
}

h4 {
  margin-bottom: 8px;
}

input {
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid teal;
}

button {
  padding: 10px;
  background: none;
  border: 1px solid teal;
  color: teal;
  cursor: pointer;
}

.post {
  width: 100%;
  padding: 15px;
  border: 2px solid teal;
  margin-bottom: 10px;
}
</style>
