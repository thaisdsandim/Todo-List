<template>
  <div>
    <AllLists />
  </div>
</template>

<script>
import AllLists from './components/AllLists.vue'

export default {
  components: {
    AllLists
}}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Bruno+Ace+SC&display=swap');

*{
  padding: 0;
  margin: 0;
  list-style: none;
  font-family: 'Bruno Ace SC', cursive;
  font-weight: 400;
}
html{
  background-color: #0DB551; 
  background-size: cover;
  text-align: center;
}
button{
  background-color: #0DB551;
  border-radius: 5px;
  border-color: black;
  border-width: 1px;
  padding: 4px;
  margin: 5px;
}
input{
  padding: 4px;
  border-radius: 5px;
  border-color: black;
  border-width: 1px;
  background-color: #ffffff00;
}
</style>