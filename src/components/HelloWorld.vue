<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-vuex" target="_blank" rel="noopener">vuex</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #app {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  #note {
    position: absolute;
    top: 50%;
    left: 50%;
    padding: 50px;
    border-radius: 5px;
    transform: translate(-50%, 50%);
  }
  #app {
    display: flex;
    font-family: Arial;
  }

  .notes {
    width: 70%;
    padding: 10px 20px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
    margin-bottom: 15px;
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-family: 'Open Sans', sans-serif;
    position: relative;
  }
  #noteContainer {
    overflow-y: scroll;
    width: 50vw;
    padding: 50px;
    height: 100vh;
    display: flex;
    flex-wrap: wrap;
    box-sizing: border-box;
    justify-content: center;
    align-content: baseline;
  }
  .notes > span {
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
    width: 66%;
  }
  .notes:first-child{
    margin-bottom: 20px;
  }
  .notes  #Capa_1 {
    height: 20px;
    width: 20px;
    fill: #ff173b;
  }
  .notes #Layer_1 {
    height: 40px;
    width: 40px;
    fill: #4e82bd;
    margin: 0 auto;
  }

  .countWord {
    color: #4b4b4b;
    font-size: 80%;
  }
</style>
