<template>
  <Tictac/>
</template>

<script>
import Tictac from './components/Tictac.vue'

export default {
  name: 'App',
  components: {
    Tictac
  }
}
</script>

<style>
:root{
  --primary: #8A4FFF;
  --dark: #131A26;
  --grey: #CCC;
  --light: #EEE;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira sans', sans-serif;
}

body{
  background-color: var(--light);
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}



</style>
