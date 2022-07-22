<template>
  <div id="app">
    <div class="urna">
      <div class="urna-teclado">
        <Teclado />

      </div>
    </div>
  </div>
</template>

<script>
import Teclado from '@/components/Teclado.vue'

export default {
  name: 'App',
  components: {
    Teclado,
  }
}
</script>

<style>
:root{
  --background-color: #333333;
  --ballot-box-background-color:#dcdde1;
  --ballot-box-keyboard-color:#2f3640;
  --ballot-box-screen-color:#e3eef9;
  --ballot-box-keyboard-button-color:#292e33;
  --ballot-box-white-button-color:#eeeeee;
  --ballot-box-correct-button-color:#ff841f;
  --ballot-box-confirm-button-color:#7daa44;
  --light-border-color:#cccccc;
  --dark-border-color:#444444;
  --light-text-color:#eeeeee;
  --dark-text-color:#333333;
}

html,body{
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
}

*{
  box-sizing: border-box;
  font-family: sans-serif;
}

button{
  border:0;
  cursor: pointer;
}

button:focus{
  outline: none;
}

button:active{
  opacity: 0.6;
}
#app{
  height: 100%;
  width: 100%;
  background-color: var(--background-color);
  display: flex;
  justify-content: center;
  align-items: center;
}
.urna{
  width: 1000px;
  height: 500px;
  background-color: var(--ballot-box-background-color);
  border-radius: 5px;
  padding: 20px;
  display: flex;
}
.urna-teclado{
  width: 40%;
  height: 100%;
  background-color: var(--ballot-box-keyboard-color);
  border-radius: 5px;
}
</style>
