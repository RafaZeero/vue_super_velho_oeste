<template>
  <div class="backdrop" @click.self="closeInstructions">
    <div class="modal">
      <slot>
        <h1>Instruções!</h1>

        <p>Aperte o botão 'começar'</p>

        <p>Clique no cowboy o mais rápido possível</p>

        <p>Caso queira voltar ao menu, clique em 'Super Velho Oeste' no topo</p>

        <button @click="closeInstructions">Fechar</button>
      </slot>
    </div>
  </div>
</template>

<script>
export default {
  props: ["header", "text"],
  emits: ["close"],
  methods: {
    closeInstructions() {
      this.$emit("close");
    },
  },
};
</script>

<style>
.modal {
  max-width: 400px;
  padding: 20px;
  margin: 200px auto;
  background: #dec590;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal h1 {
  color: #000;
  border: none;
  padding: 0;
}
.modal p {
  font-style: normal;
}
.modal .actions {
  text-align: center;
  margin: 30px 0 10px 0;
}
.modal .actions a {
  color: #333;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}
</style>