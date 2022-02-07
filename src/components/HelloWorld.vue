<template>
  <div>
    <button @click="getAll">Show All Results</button>
     <button @click="getAll">Show Result</button>
    <div class="body" v-for='post in posts' :key ="post.id">
     <h1> {{post.age}}</h1>
     <p> {{post.name}}</p>
     <h1> {{post.location}}</h1>
     <p> {{post.name}}</p>
      <p> {{post}}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      posts: []
    }
  },

  methods: {
    getAll () {
      axios.get('http://localhost:8000/api/students')
        .then((response) => {
          this.posts = response.data
          console.log(response.data)
        })
        .catch((error) => {
          console.log(error)
        })
    }
  }
}
</script>
<style scoped>
.body {
  margin: 0 auto;
  height: 20vh;
  width: 95vw;
  background-color: rgba(128, 128, 128, 0.062);
}
button {
  padding: 10px 25px;
  margin-left: 5%;
  border: none;
  margin-bottom: 5%;
  border-radius: 5px;
}
</style>
