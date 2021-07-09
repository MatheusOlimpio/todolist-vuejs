<template>
  <nav class="navbar">
    <div class="logo">
      <img src="../assets/logo.png" alt="LOGO">
      <span>Todo</span>
    </div>
    <ul class="list">
      <li><router-link :to="{name: Home}">Home</router-link></li>
      <li><router-link to="">About</router-link></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "HeaderNavbar",
};
</script>

<style scoped>
.navbar {
  width: 100%;
  height: 50px;
  padding: 0 20px;
  background: #1b263b;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  max-width: 150px;
  padding: 0 20px;
  display: flex;
  align-items: center;
}

.logo img {
  width: 40px;
}


.list {
  padding: 0 20px;
  display: flex;
}

.list li {
  margin-right: 10px;
}

</style>