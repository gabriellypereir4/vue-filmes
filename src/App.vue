<script setup>
import { reactive, onMounted } from "vue";

let filme = reactive({
  nome: "",
  capa: "",
  assistido: false,
});

let filmes = reactive([]);

function adicionarFilme() {
  filmes.push(filme);
}
</script>

<template>
  <div class="container">
    <h1>Minha lista de filmes</h1>
    <form class="formulario">
      <div class="entrada">
        <label> nome: </label>
        <input v-model="filme.nome" type="text" name="nome" />
      </div>
      <div class="entrada">
        <label> capa: </label>
        <input v-model="filme.capa" type="text" name="capa" />
      </div>
      <div class="checkbox-entrada">
        <label> assistido: </label>
        <input
          v-model="filme.assistido"
          class="assistindo"
          type="checkbox"
          name="assistido"
        />
      </div>
      <button @click.stop.prevent="adicionarFilme">registrar</button>
    </form>
    <div class="grid">
      <article v-for="(umFilme, index) in filmes">
        <img :src="umFilme.capa" alt="Filme" />
        <div class="text">
          <h3>{{ umFilme.nome }}</h3>
          <button v-if="umFilme.assistido">assistido</button>
          <button v-else>não assistido</button>
        </div>
      </article>
    </div>
  </div>
</template>

<style>
.container {
  display: flex;
  align-items: center;
  flex-direction: column;
}
.formulario {
  flex: 1;
  flex-direction: column;
  align-items: center;
  padding-bottom: 30px;
}
.entrada {
  margin-bottom: 10px;
  display: flex;
  flex-direction: column;
}
.checkbox-entrada {
  display: flex;
  margin-bottom: 10px;
}
.assistindo {
  margin-left: 10px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-gap: 20px;
  align-items: stretch;
}
.grid > article {
  border: 1px solid #ccc;
  box-shadow: 2px 2px 6px 0px rgba(0, 0, 0, 0.3);
}
.grid > article img {
  max-width: 100%;
}
.text {
  padding: 0 20px 20px;
}
.text > button {
  background: gray;
  border: 0;
  color: white;
  padding: 10px;
  width: 100%;
}
</style>
