<template>
  <p class="results">
    Tempo de reação: <b>{{ score }}</b> milissegundos
  </p>
  <p class="results">
    Pontos: <b>{{ scorePoints }}</b>
  </p>
  <p :class="this.score < 150 ? 'king' : ''" class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["score", "scorePoints"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 200) this.rank = "👑👑👑 Incomparável!! 👑👑👑";
    else if (this.score < 270)
      this.rank = "🔥🔥🔥TÁ PEGANDO FOGO BICHO!!🔥🔥🔥 ";
    else if (this.score < 330) this.rank = "😱😱 Você é muito rápido(a) 😱😱";
    else if (this.score < 600)
      this.rank = "Tá bom... mas dá pra melhorar!! 🏃🏃🏃 ";
    else if (this.score < 1300) this.rank = "Devagar e sempre 🐌🐌";
    else this.rank = "Você perdeu para o temido Va Cowboy, tente novamente";
  },
};
</script>

<style>
.results {
  font-size: 1rem;
  color: #000;
  background-color: #dec590;
  padding: 8px 16px;
  border-radius: 50px;
  border: 2px solid #5e5747;
  /* width: max-content; */
  margin: 20px auto;
}
.king {
  font-size: 2rem;
  font-weight: bold;
}
.rank {
  -webkit-text-stroke-width: 1px;
  -webkit-text-stroke-color: #000;
  -webkit-text-fill-color: #ffffff;
  margin-top: 50px;
  font-size: 2.125em;
  /* color: #fff; */
  font-weight: bold;
  max-width: 450px;
  width: fit-content;
  word-break: normal;
  /* background: #fff; */
}
</style>