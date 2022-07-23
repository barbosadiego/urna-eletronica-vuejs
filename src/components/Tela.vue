<template>
  <div class="tela">
    <div v-if="tela !== 'fim'" class="tela-votacao">
      <div class="tela-info">
        Seu voto para:
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
        <div v-if="candidatoObj" class="tela-candidato">
          <p>Nome: <span class="candidato-nome">{{ candidatoObj.nome ? candidatoObj.nome : '__________' }}</span></p>
          <p>Partido: <span class="candidato-partido">{{ candidatoObj.partido ? candidatoObj.partido : '_________' }}</span></p>
        </div>
      </div>
      <div v-if="candidatoObj.imagem" class="tela-foto-candidato">
        <img :src="candidatoObj.imagem" alt="">
      </div>
      <div v-if="candidatoObj.nome" class="tela-instrucoes">
        <p>Aperte:</p>
        <p>BRANCO para <strong>VOTAR EM BRANCO</strong></p>
        <p>LARANJA para <strong>CORRIGIR</strong></p>
        <p>VERDE para <strong>CONFIRMAR</strong></p>
      </div>
    </div>
    <div v-if="tela === 'fim'" class="tela-fim">fim</div>
  </div>
</template>

<script>
export default {
  name: 'TheTela',
  props: {
    tela: String,
    quantidadeNumeros: Number,
    candidatoNumero: String,
    candidatoObj: Object,
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
  padding: 30px 10px;
}
h1 {
  text-transform: uppercase;
}
.tela-votacao{
display: flex;
width: 100%;
flex-wrap: wrap;
}
.tela-info{
  flex: 1;
  margin-bottom: 20px;
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
.candidato-nome,
.candidato-partido{
  text-transform: uppercase;
  font-weight: bold;
}
.tela-foto-candidato img{
  width: 130px;
  border: 1px solid var(--dark-border-color);
}
.tela-instrucoes{
  width: 100%;
  border-top: 1px solid var(--dark-border-color);
}
</style>
