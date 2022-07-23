<template>
  <div class="teclado">
    <div class="numeros">
      <button @click="inserirNumero(1)">1</button>
      <button @click="inserirNumero(2)">2</button>
      <button @click="inserirNumero(3)">3</button>
      <button @click="inserirNumero(4)">4</button>
      <button @click="inserirNumero(5)">5</button>
      <button @click="inserirNumero(6)">6</button>
      <button @click="inserirNumero(7)">7</button>
      <button @click="inserirNumero(8)">8</button>
      <button @click="inserirNumero(9)">9</button>
      <button @click="inserirNumero(0)">0</button>
    </div>
    <div class="acoes">
      <button @click="votoEmBranco" class="btn-branco">BRANCO</button>
      <button @click="corrigir" class="btn-corrige">CORRIGE</button>
      <button @click="confirma" class="btn-confirma">CONFIRMA</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TheTeclado',
  props: {
    inserirNumero: Function,
    corrigir: Function,
    confirma: Function,
    votoEmBranco: Function,
  },
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
