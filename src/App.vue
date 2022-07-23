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
        <Teclado :inserirNumero="inserirNumero" />
      </div>
    </div>
  </div>
</template>

<script>
import Teclado from '@/components/Teclado.vue';
import Tela from '@/components/Tela.vue';

export default {
  name: 'App',
  components: {
    Teclado,
    Tela,
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
  methods: {
    inserirNumero(numero) {
      if (this.candidatoNumero.length === this.quantidadeNumeros) {
        return false
      }
      this.candidatoNumero += '' + numero;
      this.exibirCandidato()
    },
    exibirCandidato(){
      if (this.candidatoNumero.length < this.quantidadeNumeros) return false;

      if (this.candidatos[this.tela][this.candidatoNumero]) {
        this.candidatoObj = this.candidatos[this.tela][this.candidatoNumero];
      }
    }
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
  justify-content: center;
  align-items: center;
}
.urna {
  width: 1000px;
  height: 500px;
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
</style>
