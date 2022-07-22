<template>
  <div class="teclado">
    <div class="numeros">
      <button>1</button>
      <button>2</button>
      <button>3</button>
      <button>4</button>
      <button>5</button>
      <button>6</button>
      <button>7</button>
      <button>8</button>
      <button>9</button>
      <button>0</button>
    </div>
    <div class="acoes">
      <button class="btn-branco">BRANCO</button>
      <button class="btn-corrige">CORRIGE</button>
      <button class="btn-confirma">CONFIRMA</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TheTeclado',
  props: {},
};
</script>

<style scoped>
.teclado{
  width: 100%;
  height: 100%;
  display: grid;
  align-items: center;
  padding: 20px;
}
.numeros{
  display: grid;
  justify-items: center;
  grid-template-columns: repeat(3,1fr);
  gap: 10px;
}
.numeros button{
  font-size: 2.2rem;
}
.numeros button:last-child{
  grid-column: 2;
}
.teclado button{
  width: 100%;
  height: 60px;
  border-radius: 5px;
  background-color: var(--ballot-box-keyboard-button-color);
  color: var(--light-text-color);
}
.acoes{
  display: flex;
  gap: 10px;
}
.acoes button{
  color: var(--dark-text-color);
  font-size: 1rem;
  font-weight: bold;
}
.acoes .btn-branco{
  background-color: var(--ballot-box-white-button-color);
}
.acoes .btn-corrige{
  background-color: var(--ballot-box-correct-button-color);
}
.acoes .btn-confirma{
  background-color: var(--ballot-box-confirm-button-color);
}
</style>
