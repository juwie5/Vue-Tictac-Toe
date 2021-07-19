<template>
  <Board/>
</template>

<script>
import Board from './components/Board.vue'

export default {
  name: 'App',
  components: {
    Board
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
