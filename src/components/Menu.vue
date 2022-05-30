<template>
  <div class="menu_container">
    <h1 class="menu_items" @click="closeMenu">Jogar</h1>
    <h2 class="menu_items" @click="toggleInstructions">Instruções</h2>
    <h2 class="menu_items" @click="underConstruction">Pontuações</h2>
  </div>
  <div v-if="showInstructions">
    <Instructions @close="toggleInstructions" />
  </div>
</template>

<script>
import Instructions from "./Instructions";

export default {
  props: ["showMenu"],
  components: { Instructions },
  data() {
    return {
      showInstructions: false,
    };
  },
  methods: {
    closeMenu() {
      this.$emit("closeGameMenu", this.closeGameMenu);
    },
    toggleInstructions() {
      this.showInstructions = !this.showInstructions;
    },
    underConstruction() {
      confirm("Em Construção!!");
    },
  },
};
</script>

<style>
.menu_container {
  background-image: url("../../public/img/bg_menu_frame.png");
  background-repeat: no-repeat;
  background-size: contain;

  height: 45rem;
  max-width: 52rem;

  display: flex;
  flex-direction: column;

  margin: 0 auto;
  justify-content: center;
  align-items: center;
}

@media (max-width: 426px) {
  .menu_container {
    background-image: url("../../public/img/bg_menu_cell.png");
    background-repeat: no-repeat;
    background-size: cover;
    height: 30rem;
    display: flex;
    flex-direction: column;
  }
  .menu_items {
    color: #000 !important;
    font-size: 2.25em;
  }
}
.menu_items {
  color: #fff;
  font-size: 2.25em;
  cursor: pointer;
}
.menu_items:hover {
  font-size: 2.5em;
}
</style>