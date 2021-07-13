<template>
  <div>
    <header>
      <h1>Tic Tac toe</h1>
      </header>
      <main>
        <section class="board turn-x" id="board">
            <div class="cell x"></div>
            <div class="cell o"></div>
            <div class="cell"></div>
            <div class="cell"></div>
            <div class="cell"></div>
            <div class="cell"></div>
            <div class="cell"></div>
            <div class="cell"></div>
            <div class="cell"></div>
        </section>
      </main>
  </div>
</template>

<script>
export default {
  name: 'Tictac',

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
  font-size: 42PX;
  text-transform: uppercase;
  text-shadow: -4px 1px var(--primary);
}

main {
  display: flex;
  align-items: center;
  justify-content: center;
  flex: 1 1 0%;
  padding-top: 100px;
}

.board {
  display: grid;
  grid-template-columns: repeat(3, auto);
}

.cell{
  position: relative;
  border: 1px solid var(--dark);
  width: 100px;
  padding-top: 100%;
}

.cell:nth-child(1),
.cell:nth-child(2),
.cell:nth-child(3){
  border-top: none;

}

.cell:nth-child(1),
.cell:nth-child(4),
.cell:nth-child(7){
  border-left: none;
}

.cell:nth-child(7),
.cell:nth-child(8),
.cell:nth-child(9){
  border-bottom: none;
}

.cell:nth-child(3),
.cell:nth-child(6),
.cell:nth-child(9){
  border-right: none;
}

.cell.x::after,
.cell.x::before,
.board.turn-x .cell:hover::after,
.board.turn-x .cell:hover::before{
  content: '';
  display: block;
  position: absolute;
  top: 50%;
  left: 50%;
  width: 10px;
  height: 90px;
  background-color: var(--dark);
  border-radius: 99px;
}

.cell.x::before, 
.board.turn-x .cell:hover::before{
  transform: translate(-50%, -50%) rotate(-45deg);
}

.cell.x::after,
.board.turn-x .cell:hover::after{
  transform: translate(-50%, -50%) rotate(45deg);
}

.cell.o::before{
   content: '';
   display: block;
   position: absolute;
   top: 50%;
   left: 50%;
   transform: translate(-50%, -50%);
   width: 60px;
   height: 60px;
   border: 10px solid var(--dark);
   border-radius: 50%;
}

.board.turn-x .cell:hover::after,
.board.turn-x .cell:hover::before {
  background-color: var(--grey);
  
}

  

</style>
