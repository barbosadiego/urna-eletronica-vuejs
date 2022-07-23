<template>
  <div class="tela">
    <div v-if="tela !== 'fim'" class="votacao">
      <p>Seu voto para:</p>
      <h1>{{ tela }}</h1>
      <div class="tela-numeros">
        Números:
        <div
          class="tela-numero"
          v-for="(value, key) in candidatoNumero.padEnd(quantidadeNumeros, ' ')"
          :key="key"
        >
          {{ value }}
        </div>
      </div>
    </div>
    <div v-if="tela === 'fim'" class="fim">fim</div>
  </div>
</template>

<script>
export default {
  name: 'TheTela',
  props: {
    tela: String,
    quantidadeNumeros: Number,
    candidatoNumero: String,
  },
};
</script>

<style scoped>
.tela {
  width: 100%;
  height: 100%;
  background-color: var(--ballot-box-screen-color);
  border-radius: 5px;
  border: 2px solid var(--light-border-color);
  padding: 10px;
}
h1 {
  text-transform: uppercase;
}
.tela-numeros {
  display: flex;
  align-items: center;
  gap: 10px;
}
.tela-numero{
  width: 40px;
  height: 50px;
  border: 1px solid var(--dark-border-color);
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
