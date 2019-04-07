<template>
  <div id="app">
    <game id="game"></game>
    <click id="footer"></click>
  </div>
</template>

<script>
import game from './components/game';
import click from './components/click';

export default {
  name: 'app',
  components: {
    game,
    click
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
* {
  margin: 0;
  padding: 0;
}
html, body, #app {
  height: 100%;
}
#app {
  display: flex;
  flex-direction: column;
}
#game {
  flex: 1 0 auto;
}
#footer {
  flex-shrink: 0;
}

</style>
