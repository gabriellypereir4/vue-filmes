<script setup>
import { reactive, onMounted } from "vue";

let filme = reactive({
  nome: "",
  capa: "",
  assistido: false,
});

// functions that mutate state and trigger updates
function increment() {
  count.value++;
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
      <button>registrar</button>
    </form>
    {{ JSON.stringify(filme) }}
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
</style>
