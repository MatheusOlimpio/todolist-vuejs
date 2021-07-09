<template>
  <div id="nav">
    <HeaderNavbar />
  </div>
  <main>
    <transition mode="out-in">
      <router-view />
    </transition>
  </main>
</template>

<script>
import HeaderNavbar from "@/components/HeaderNavbar.vue";
export default {
  name: "app",
  components: {
    HeaderNavbar,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  height: 100vh;
  color: #778da9;
  background: #0d1b2a;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
}

main {
  max-width: 900px;
  margin: 0 auto;
  padding: 20px;
}

ul {
  list-style-type: none;
}

input,
textarea {
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #0d1b2a;
  box-shadow: 0 1px 3px #0d1b2a;
  font-size: 1rem;
  margin: 10px 0;
  color: #778da9;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
}

textarea {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  resize: none;
}

.router-link-active {
  color: #778da9;
  text-decoration: none;
}

.router-link-active:hover {
  color: #e0e1dd;
}

.v-enter-active,
.v-leave-active {
  transition: all 0.3s;
}

.v-enter-active {
  animation: 0.2s fadeIn forwards;
}

.v-leave-active {
  animation: 0.2s fadeOut forwards;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translate3d(-30px, 0, 0);
  }

  to {
    transform: translate3d(0px, 0, 0);
    opacity: 1;
  }
}

@keyframes fadeOut {
  from {
    transform: translate3d(0px, 0, 0);
  }

  to {
    transform: translate3d(30px, 0, 0);
    opacity: 0;
  }
}

.btn {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  font-size: 1rem;
  padding: 10px;
  background: #ffcf33;
  border: none;
  cursor: pointer;
  font-weight: bold;
}

.danger {
  color: white;
  background: red;
}
</style>
