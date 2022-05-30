<template>
  <h1 class="game_title" @click="toggleMenu">Super Velho Oeste</h1>
  <Menu
    v-if="showMenu"
    @startGame="startGame"
    :showMenu="showMenu"
    @closeGameMenu="closeGameMenu"
  />
  <div v-else class="bg_temp">
    <h2>Seja mais rápido que o vilão!!</h2>
    <button @click="startGame" :disabled="isPlaying">Começar</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Results v-if="showResults" :score="score" :scorePoints="scorePoints" />
  </div>
</template>

<script>
import Block from "./components/Block";
import Results from "./components/Results";
import Menu from "./components/Menu";

export default {
  name: "App",
  components: { Block, Results, Menu },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      scorePoints: null,
      showResults: false,
      showMenu: true,
      scorePointsList: [],
    };
  },
  methods: {
    startGame() {
      // set time amount (ms)
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame({ reactionTime, totalPoints }) {
      this.score = reactionTime;
      this.scorePoints = totalPoints;
      this.isPlaying = false;
      this.showResults = true;
      this.scorePointsList.push(this.scorePoints);
      localStorage.setItem(
        "scorePointsList",
        JSON.stringify(this.scorePointsList)
      );
      setTimeout(() => {
        this.showResults = false;
      }, 10 * 1000);
    },
    closeGameMenu() {
      this.showMenu = false;
    },
    toggleMenu() {
      this.showMenu = true;
    },
  },
  mounted() {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 15px;
}
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background: url("../public/img/bg_main.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  height: 100%;
}
@media (max-width: 769px) {
  body {
    background-position: top;
    background-size: 280%;
  }
}
button {
  background: #5e5747;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
.game_title {
  font-size: 2rem;
  /* color: #5e5747; */
  background-color: #dec590;
  padding: 8px 16px;
  -webkit-text-stroke-width: 1px;
  -webkit-text-stroke-color: #000;
  -webkit-text-fill-color: #ffffff;
  border-radius: 50px;
  border: 2px solid #5e5747;
  width: max-content;
  margin: 0 auto 10px;
}
.bg_temp {
  background: #dec590e4;
  border-radius: 35px;
  margin: 0 auto;
  padding: 2rem;
  width: fit-content;
  height: 500px;
}
</style>