<template>
  <div id="app">
    <nav>
    <div id='navItems'>
    <h1 @click="createBotView()">Create</h1>
    <h1>Battle Bots</h1>
    <h1 @click="botListView()">Collection</h1>
    </div>
    </nav>

    <createbot v-if='createBot' :bots='bots' :createABot='createABot' :botListView='botListView'></createbot>
    <botlist v-else :bots="bots" :retireBot='retireBot'></botlist>

  </div>
</template>

<script>
import CreateBot from "./CreateBot.vue";
import BotList from "./BotList.vue";

export default {
  components: {
    createbot: CreateBot,
    botlist: BotList
  },
  data() {
    return {
      createBot: true,
      bots: [{id: 0, botName: 'bob', attackValue: 123, healthValue: 354}, {id: 1, botName: 'drew', attackValue: 123, healthValue: 354} ]
    };
  },
  methods: {
    createBotView() {
      this.createBot = true;
    },
    botListView() {
      this.createBot = false;
    },
    createABot(bot) {
      this.bots.push(bot)
    },
    retireBot(id) {
      this.bots.splice(id, 1)
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0;
  height: 100vh;
  width: 100%;
  background: #42b983;
}

nav {
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 100px;
  background: darkblue;
  align-items: flex-end;
  justify-content: center;
  color: white;
}

#navItems {
  width: 75%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
