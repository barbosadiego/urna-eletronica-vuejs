<template>
  <div id="app">
    <div class="urna">
      <div class="urna-tela">
        <Tela
          :tela="tela"
          :candidatoNumero="candidatoNumero"
          :quantidadeNumeros="quantidadeNumeros"
          :candidatoObj="candidatoObj"
        />
      </div>
      <div class="urna-teclado">
        <Teclado 
          :inserirNumero="inserirNumero"
          :corrigir="corrigir"
          :confirma="confirma"
          :votoEmBranco="votoEmBranco"
        />
      </div>
    </div>
    <div class="lista">
      <h1>Candidatos</h1>
      <div>
        <h2>Prefeito: ASH</h2>
        <span>Número: 01</span>
        <h2>Prefeito: VEGETA</h2>
        <span>Número: 08</span>
      </div>
      <div>
        <h2>Vereador: PIKACHU</h2>
        <span>Número: 01234</span>
        <h2>Vereador: GOKU</h2>
        <span>Número: 08001</span>
      </div>
      
    </div>
  </div>
</template>

<script>
import Teclado from '@/components/Teclado.vue';
import Tela from '@/components/Tela.vue';
import ConfirmAudio from '@/assets/confirm.wav';
import KeyAudio from '@/assets/key.wav';

export default {
  name: 'App',
  components: {
    Teclado,
    Tela,
  },
  methods: {
    inserirNumero(numero) {
      this.ativarSom(KeyAudio)
      if (this.candidatoNumero.length === this.quantidadeNumeros) {
        return false
      }
      this.candidatoNumero += '' + numero;
      this.exibirCandidato();
    },
    exibirCandidato(){
      if (this.candidatoNumero.length < this.quantidadeNumeros) return false;

      if (this.candidatos[this.tela][this.candidatoNumero]) {
        this.candidatoObj = this.candidatos[this.tela][this.candidatoNumero];
        return true
      }

      this.candidatoObj.nome = 'Voto nulo'
      this.candidatoObj.partido = 'Voto nulo'
    },
    corrigir(){
      this.ativarSom(KeyAudio)
      this.candidatoNumero = '';
      this.candidatoObj = {};
    },
    confirma(){
      if (this.tela === 'prefeito' && this.candidatoNumero.length === this.quantidadeNumeros) {
        this.ativarSom(ConfirmAudio)
        this.tela = 'vereador';
        this.quantidadeNumeros = 5;
        this.limparTela();
        return true
      }
      if (this.tela === 'vereador' && this.candidatoNumero.length === this.quantidadeNumeros) {
        this.ativarSom(ConfirmAudio)
        this.tela = 'fim';
        this.limparTela();

        const context = this;

        setTimeout(() => {
          context.tela = 'prefeito';
          context.quantidadeNumeros = 2;
          context.candidatoObj = {};
        }, 2000);
      }
    },
    limparTela(){
      this.candidatoNumero = '';
      this.candidatoObj = {};
    },
    votoEmBranco(){
      this.ativarSom(KeyAudio)
      this.candidatoObj.nome = 'VOTO EM BRANCO';
      this.candidatoObj.partido = 'VOTO EM BRANCO';
      this.candidatoNumero = '--'
      if(this.tela === 'vereador') this.candidatoNumero = "-----"
    },
    ativarSom(url){
      const audio = new Audio(url);
      audio.play();
    }
  },
  data() {
    return {
      tela: 'prefeito',
      quantidadeNumeros: 2,
      candidatoNumero: '',
      candidatoObj: {},
      candidatos: {
        prefeito: {
          '01': {
            nome: 'Ash',
            partido: 'Pokemon',
            imagem:
              'https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/ash.png',
          },
          '08': {
            nome: 'Vegeta',
            partido: 'Dragon Ball',
            imagem:
              'https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/vegeta.png',
          },
        },
        vereador: {
          '01234': {
            nome: 'Pikachu',
            partido: 'Pokemon',
            imagem:
              'https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/pikachu.png',
          },
          '08001': {
            nome: 'Goku',
            partido: 'Dragon Ball',
            imagem:
              'https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/goku.png',
          },
        },
      },
    };
  },
};
</script>

<style>
:root {
  --background-color: #333333;
  --ballot-box-background-color: #dcdde1;
  --ballot-box-keyboard-color: #2f3640;
  --ballot-box-screen-color: #e3eef9;
  --ballot-box-keyboard-button-color: #292e33;
  --ballot-box-white-button-color: #eeeeee;
  --ballot-box-correct-button-color: #ff841f;
  --ballot-box-confirm-button-color: #7daa44;
  --light-border-color: #cccccc;
  --dark-border-color: #444444;
  --light-text-color: #eeeeee;
  --dark-text-color: #333333;
}

html,
body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
}

* {
  box-sizing: border-box;
  font-family: sans-serif;
}

button {
  border: 0;
  cursor: pointer;
}

button:focus {
  outline: none;
}

button:active {
  opacity: 0.6;
}
#app {
  height: 100%;
  width: 100%;
  background-color: var(--background-color);
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.urna {
  width: 1000px;
  height: 500px;
  margin-left: auto;
  margin-right: auto;
  background-color: var(--ballot-box-background-color);
  border-radius: 5px;
  padding: 20px;
  display: flex;
  justify-content: space-between;
}
.urna-teclado {
  width: 40%;
  height: 100%;
  background-color: var(--ballot-box-keyboard-color);
  border-radius: 5px;
}
.urna-tela {
  width: 55%;
  height: 100%;
}
.lista{
  background-color: var(--ballot-box-background-color);
  width: 300px;
  height: 100%;
  padding: 20px;
}
</style>
