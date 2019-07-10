<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>Vue JS Get Data from API By Axios</h1>
    <div>
      <div class="post" v-for="post in posts"  :key="post.id">
        <h3>Title: {{ post.title }}</h3>
        <p>Description: {{ post.body }}</p>
      </div >
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
      return {
         posts: []
      }
    },
    mounted() {
      var self = this;
      axios.get('http://jsonplaceholder.typicode.com/posts')
      .then( function(res){
        self.posts =  res.data;
        console.log('Data: ', res.data);
      })
      .catch(function(error){
        console.log('Error:' ,error);
      })
    }
}
</script>

<style scoped>

.post{
    background: #ccc;
    margin-bottom: 20px;
    padding: 10px 20px;
}

h3 {
  text-align: left;
}

p{
  text-align: left;
}
</style>
