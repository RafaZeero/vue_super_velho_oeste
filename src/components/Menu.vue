<template>
  <div class="menu_container">
    <h1 class="menu_items" @click="closeMenu">Jogar</h1>
    <h2 class="menu_items">Instruções</h2>
    <h2 class="menu_items">Pontuações</h2>
  </div>
</template>

<script>
export default {
  props: ["showMenu"],
  methods: {
    closeMenu() {
      this.$emit("closeGameMenu", this.closeGameMenu);
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
    -webkit-text-stroke-width: 1px;
    -webkit-text-stroke-color: #000;
    -webkit-text-fill-color: #ffffff;
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