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
      console.log("close menu");
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
  /* padding: 200px; */
  border: 1px solid #f78942;
}

@media (max-width: 426px) {
  .menu_container {
    background: url("../../public/img/bg_menu_cell.png");
    background-repeat: no-repeat;
    background-size: cover;
    height: 30rem;
    border: 1px solid #f45612;
    display: flex;
    flex-direction: column;
  }
  .menu_items {
    /* color: #eb6226; */
    color: #5e5747;
    text-shadow: -2px 1px #eb6226;
    font-size: 2.25em;
    border: 1px solid #1bde6c;
  }
}
.menu_items {
  color: #fff;
  font-size: 2.25em;
  border: 1px solid #f45612;
  cursor: pointer;
}
.menu_items:hover {
  font-size: 2.5em;
}
</style>