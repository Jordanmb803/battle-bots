<template>
    <div id=createBot>
        <input v-model="botName" placeholder="Bot Name*">
        <input v-model="attackValue" placeholder="Attack Value*">
        <input v-model="healthValue" placeholder="Health Value*">
        <div class="buttonDiv">
        <button @click="submitBot()">SUBMIT</button>
        <button @click="clearFields()">CLEAR</button>
        </div>
    </div>
</template>

<script>
export default {
  props: ["createABot", "botListView", "bots"],
  data() {
    return {
      id: 0,
      botName: "",
      attackValue: "",
      healthValue: ""
    };
  },
  methods: {
      submitBot(){
          let id = this.bots.length
          this.createABot({id: id, botName: this.botName, attackValue: this.attackValue, healthValue: this.healthValue})
          this.botName = '',
          this.attackValue = '',
          this.healthValue = ''
          this.botListView()
      },
      clearFields(){
          this.botName = '',
          this.attackValue = '',
          this.healthValue = ''
      }
  }
  
};
</script>

<style>
#createBot {
  margin-left: auto;
  margin-right: auto;
  margin-top: 100px;
  width: 40%;
  height: 35%;
  background: white;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
}

input {
  margin: 5px;
  height: 10%;
  width: 85%;
  border-bottom: black solid 1px;
  border-top: none;
  border-right: none;
  border-left: none;
  background: white;
}

.buttonDiv {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    width: 100%;
    height: 35px;
}

button {
  width: 30%;
}
</style>
