<template>
  <div class="cadastro">
    <form @submit.prevent="$emit('on-submit', form)">
      <input
        type="text"
        id="name"
        name="name"
        v-model="form.name"
        placeholder="Escreva aqui uma tarefa"
        required
      />
      <textarea
        type="text"
        id="description"
        name="description"
        v-model="form.description"
        rows="4"
        placeholder="Descricao da tarefa"
        required
      ></textarea>
      <div class="form-button">
        <slot></slot>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "FormularioLista",
  props: {
    task: {
      type: Object,
    },
  },
  data() {
    return {
      form: {
        name: this.task?.name || "",
        description: this.task?.description || "",
      },
    };
  },
};
</script>

<style scoped>
.cadastro {
  margin-top: 20px;
  padding: 10px 20px;
  margin-top: 30px;
  background: #1b263b;
  border-radius: 2px;
  border-left: 2 px solid #e0e1dd;
}
.cadastro h1 {
  text-align: left;
}

form {
  display: grid;
  width: 100%;
}

input[type="text"]:focus,
textarea:focus {
  background: #e0e1dd !important;
  color: #0d1b2a;
}

.cadastro input,
.cadastro textarea {
  background: #1b263b;
}

.form-button {
  width: 100%;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 10px;
  /* flex-wrap: wrap;
  justify-content: flex-start; */
  padding: 10px;
}

.form-button button {
  margin: 10px;
}
</style>