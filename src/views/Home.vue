<template>
  <div class="home">
    <transition>
      <ListToDo />
    </transition>
  </div>
</template>

<script>
// @ is an alias to /src
import ListToDo from "@/components/ListToDo.vue";
export default {
  name: "Home",
  components: {
    ListToDo,
  },
};
</script>
