<template>
  <div>
    <header>
      <h1>Tic Tac toe</h1>
      </header>
      <main class="head">
        <h2>{{ calculateWinner }}</h2>
        <section class="board">
              <span class='vertical-line-1'></span>
              <span class='vertical-line-2'></span>
              <Square
                v-for="(square, i) in board"
                :key="`square-${i}`"
                :label="`square-${i}`"  
                :value="square"
                @click="markSquare(i)"
                :winner="calculateWinner"
              />
        </section>
        <input type="button" @click="reset" value="Reset">
      </main>
  </div>
</template> 

<script>
import Square from './Square';
import {ref} from 'vue';
import { useCalculateWinner } from '../utils/calWinner';


export default {
  components: {
    Square,
  },
  
setup(){
  const board = ref(Array(9).fill(null));
  const playerValue = ref('X');
  const {calculateWinner} = useCalculateWinner(board);

  const markSquare = (i) => {
    const boardCopy = board.value.slice();
    boardCopy[i] = playerValue.value;
    board.value = boardCopy;
    playerValue.value === 'X' ? (playerValue.value = 'O') : (playerValue.value = 'X');
   };
  
  const reset = () => {
        board.value = Array(9).fill(null);
        playerValue.value = 'X';
    };

   return {
     board,
     playerValue,
     markSquare,
     calculateWinner,
     reset
   }
}
};

 
</script>

<style>
header{
  background-color: var(--dark);
  padding: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-bottom: 3px solid var(--primary);
}

header h1{
  color: #FFF;
  font-size: 42px;
  text-transform: uppercase;
  text-shadow: -4px 1px var(--primary);
}
h2 {
  margin-bottom: 30px;
}


main {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  flex: 1 1 0%;
  padding-top: 100px;
}

.board {
  display: grid;
  position: relative;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
}

.board::before, .board::after {
 background: var(--dark);
}

.vertical-line-1, .vertical-line-2 {
     background: var(--dark);
}

.board::before, .board::after {
    content: '';
    width: 100%;
    height: 5px;
    position: absolute;
    border-radius: 1rem;
}

.board::before {
    top: 33%;
}

.board::after {
    top: 66%;
}

.vertical-line-1, .vertical-line-2 {
    position: absolute;
    width: 100%;
    height: 1px;
    top: 50%;
    border-radius: 1rem;
    transform: translate(-50%, -50%) rotate(90deg);
}

.vertical-line-1 {
    left: 33%;
}

.vertical-line-2 {
    left: 66%;
}

input {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px;
  font-family: 'Fira sans', sans-serif;
  font-size: 18px;
  font-weight: 700;
  text-align: center;
  color: var(--light);
  background-color: var(--dark);
  border: none;
  border-radius: 3px;
  margin-top: 25px;
}

  
</style>
