<template>
  <div id="app">
    <div class="form">
      <h1>Создание поста</h1>
      <div>
        <input 
          v-model="title"
          type="text" 
          placeholder="Название поста"
        >
      </div>
      <div>
        <input
          v-model="text"
          type="text"
          placeholder="Содержание поста"
        >
      </div>
      <button @click="addPost">Добавить пост</button>
    </div>

    <div class="posts">
      <h2>Список постов</h2>
      <div v-if="posts.length === 0">
        Добавленных постов нет
      </div>
      <div 
        v-for="(post, index) in posts"
        :key="index"
        class="post"
      >
        <div style="display: flex; justify: space-between; align-items: center;">
          <div style="width: 90%;">
            <h4>Название поста: {{ post.title }}</h4>
            <p><strong>Содержание поста:</strong> {{ post.text }}</p>
          </div> 

          <div>
            <button 
              style="border: 1px solid red; color: red;"
              @click="deletePost(index)"
            >
              Удалить
            </button>
          </div>
        </div>
      </div>
    </div>

    
  
    <!-- <div>
      Количество лайков: {{ likes }}
    </div>
    <div>
      Количество дизлайков: {{ dislikes }}
    </div>
    <div>
      <button class="like" @click="addLike">Лайк</button>
      <button class="dislike" @click="addDislike">Дизлайк</button>
    </div> -->
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      title: '',
      text: '',
      likes: 0,
      dislikes: 0,
      posts: [
        {
          id: 1,
          title: 'Пост №1',
          text: 'Текст поста №1',
        },
        {
          id: 2,
          title: 'Пост №2',
          text: 'Текст поста №2',
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
    addPost() {
      this.posts.push({
        title: this.title,
        text: this.text,
      });
      this.title = this.text = '';
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
