<template>
  <p>Tempo de reação: {{ score }} milissegundos</p>
  <p :class="this.score < 150 ? 'king' : ''" class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 150) this.rank = "👑👑👑 Incomparável!! 👑👑👑";
    else if (this.score < 240)
      this.rank = "🔥🔥🔥TÁ PEGANDO FOGO BICHO!!🔥🔥🔥 ";
    else if (this.score < 330) this.rank = "😱😱 Você é muito rápido(a) 😱😱";
    else if (this.score < 600)
      this.rank = "Tá bom... mas dá pra melhorar!! 🏃🏃🏃 ";
    else if (this.score < 1000) this.rank = "Devagar e sempre 🐌🐌";
    else if (this.score < 2500)
      this.rank = "Você sabe onde fica o mouse?? 😂😂😂😂";
    else this.rank = "";
  },
};
</script>

<style>
.king {
  font-size: 2rem;
  font-weight: bold;
}
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>