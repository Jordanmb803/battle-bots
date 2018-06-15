<template>
    <div id='botList'>
      <div id='selectedBox'>
        <div v-if="selected === 0">
          <h2 >Bot #1: Select a bot below </h2>
          <h2 >Bot #2: Select a bot below</h2>
        </div>
        <div v-else-if="selected === 1">
          <h2 >Bot #1: {{firstSelected}}</h2>
          <h2 >Bot #2: Select a bot below</h2>
        </div>
        <div v-else>
          <h2 >Bot #1: {{firstSelected}}</h2>
          <h2 >Bot #2: {{secondSelected}}</h2>
        </div>
        <div class='buttonDiv' id='battleClear'>
          <button @click="battle()">BATTLE</button>
          <button @click="clear()">CLEAR</button>
        </div>
      </div>
        <div class='collection'>
          <div v-for="bot in bots" :key="bot.id" class='bot'>
            <h2>{{bot.botName}}</h2>
            <p>Attack: {{bot.attackValue}}</p>
            <p>Health: {{bot.healthValue}}</p>
            <div class='buttonDiv'>
              <h3 @click="selectBot(bot.botName)" >Select</h3> <h3 @click="retireBot(bot.id)">Retire</h3>
            </div>
          </div>
        </div>
      </div>
</template>

<script>
export default {
  props: ["bots", "retireBot"],
  data() {
    return {
      selected: 0,
      firstSelected: "",
      secondSelected: ""
    };
  },
  methods: {
    selectBot(botName) {
      if (this.selected === 0) {
        this.firstSelected = botName;
        this.selected++;
      } else if (this.selected === 1) {
        this.secondSelected = botName;
        this.selected = 2;
      }
    },
    clear() {
      (this.selected = 0),
        (this.firstSelected = ""),
        (this.secondSelected = "");
    },
    battle() {
      let randomNum = Math.random();
      console.log(randomNum)
      if (this.selected === 0) {
        alert("Please select 2 bots to battle!");
      } else if (randomNum < 0.5) {
        alert(this.firstSelected + " won the battle!");
      } else if (randomNum > 0.5 ) {
        alert(this.secondSelected + " won the battle!");
      }
    }
  }
};
</script>

<style scope>
#botList {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  width: 100%;
}

#selectedBox {
  height: 160px;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.collection {
  display: flex;
  flex-direction: row;
  justify-content: center;
}

h2 {
  margin: 10px 5px 10px 5px;
}

#battleClear {
  height: 50px;
  width: 40%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

button {
  width: 40%;
}

.bot {
  margin-top: 50px;
  margin-right: 20px;
  margin-left: 20px;
  display: flex;
  flex-direction: column;
  background: white;
  width: 20%;
}
</style>
