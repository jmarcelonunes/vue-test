<template>
  <div id="app">
    <Header />
    <AddAdvantage v-on:add-advantage="addAdvantage" />
    <Advantages v-bind:advantages="advantages" v-on:del-advantage="deleteAdvantage"/>
  </div>
</template>

<script>
import Advantages from './components/Advantages.vue'
import AddAdvantage from './components/AddAdvantage.vue'
import Header from './components/Layout/Header.vue'
import axios from 'axios'
export default {
  name: 'App',
  components: {
    Header,
    AddAdvantage,
    Advantages
  },
  data(){
    return{
      advantages: [
      ]
    }
  },
  methods: {
    deleteAdvantage(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(this.advantages = this.advantages.filter(a => a.id !== id))
      .catch(err => console.log(err))
      
    },
    addAdvantage(advantage){
      const { title, completed } = advantage;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      }).then(data => this.advantages = [...this.advantages, data.data])
      .catch(err => console.log(err))
      
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=4')
    .then(data => this.advantages = data.data)
    .catch(err => console.log(err));
  }
}
</script>

<style>
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body{
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn{
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover{
    background: #666;
  }
</style>
