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
        {
          id: 1,
          title: 'Flexibilidade',
          completed: false
        },
        {
          id: 2,
          title: 'Fácil entendimento',
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteAdvantage(id){
      this.advantages = this.advantages.filter(a => a.id !== id)
    },
    addAdvantage(advantage){
      this.advantages = [...this.advantages, advantage]
    }
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
