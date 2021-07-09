<template>
  <div>
    <h1>Lista</h1>
    <div v-if="list.length > 0" key="list">
      <ul>
        <transition-group name="swap" mode="out-in">
          <li class="list_item" v-for="item in list" :key="item.id">
            <div class="item_fields">
              <input class="item_field iitem_name" v-model="item.name" />
              <textarea
                class="item_field item_description"
                v-model="item.description"
              ></textarea>
              <p class="item_date">Criada em: {{ formataData(item.date) }}</p>
            </div>
            <div class="item_buttons">
              <button class="btn-edit"></button>
              <button class="btn-delete" @click="deleteTask(item.id)">X</button>
            </div>
          </li>
        </transition-group>
      </ul>
    </div>
    <div v-else key="listEmpty">
      <span>Nenhum item adicionado a lista</span>
    </div>
    <button v-if="!newTask" class="btn" @click="newTask = true">
      Adicionar nova tarefa
    </button>
    <transition>
      <FormularioLista @on-submit="addTask" v-if="newTask">
        <button type="submit" class="btn">Cadastrar</button>
        <button type="reset" class="btn btn-cancel" @click="newTask = false">
          Cancelar
        </button>
      </FormularioLista>
    </transition>
  </div>
</template>

<script>
import { api } from "@/services.js";
import FormularioLista from "@/components/FormularioLista.vue";
export default {
  name: "ListToDo",
  components: {
    FormularioLista,
  },
  data() {
    return {
      list: {},
      newTask: false,
    };
  },
  methods: {
    getLista() {
      api.get("/list").then((response) => {
        this.list = response.data;
      });
    },
    addTask(data) {
      data.date = new Date();
      api.post("/list", data).then(() => {
        this.getLista();
        this.newTask = false;
      });
    },
    deleteTask(id) {
      if (confirm("Tem certeza que deseja excluir a tarefa?")) {
        api.delete(`/list/${id}`).then(() => {
          this.getLista();
        });
      }
    },
    formataData(date) {
      const dateToFormat = new Date(date);
      return new Intl.DateTimeFormat("pt-BR", {
        day: "numeric",
        month: "numeric",
        year: "numeric",
        hour: "numeric",
        minute: "numeric",
      }).format(dateToFormat);
    },
  },
  created() {
    this.getLista();
  },
};
</script>

<style scoped>
.list_item {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-top: 20px;
  background: #1b263b;
  padding: 10px 20px;
  border-radius: 2px;
  border-left: 2px solid #e0e1dd;
}

.item_fields {
  width: 100%;
}

.item_field {
  color: #778da9;
  background: #1b263b;
  border: none;
  box-shadow: none;
  padding: 0;
  width: 100%;
  font-size: 1rem;
}

.item_name {
  width: 100%;
}

.item_description {
  margin: 0;
}

.item_description:focus {
  background: #1b263b;
}

.btn {
  margin-top: 20px;
}

.btn-delete {
  border: none;
  border-radius: 3px;
  background: none;
  color: white;
  padding: 10px;
  cursor: pointer;
}

.btn-cancel {
  border: 2px solid #ffcf33;
  color: #ffcf33;
  background: none;
}

.btn-edit {
  background: url(../assets/edit-button.svg) no-repeat center center;
  background-size: 150px 150px;
  border: none;
  cursor: pointer;
}

.btn-delete:hover {
  background: rgba(13, 27, 42, 0.2);
}

.swap-enter-active,
.swap-leave-active {
  transition: all 0.3s;
}

.swap-enter-active {
  animation: 0.2s fadeIn forwards;
}

.swap-leave-active {
  animation: 0.2s fadeOut forwards;
}
</style>