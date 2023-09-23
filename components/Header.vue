<template>
  <header class="header">
    <router-link to="/" class="header-link"
      ><h1 class="header__title">shrtnr.</h1></router-link
    >
  </header>
</template>

<script>
export default {};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: center;
  padding: 40px 0;
}

.header__title {
  margin: 0;
  font-size: 47px;
  font-weight: 700;
  color: #2f80ed;
}

.header-link {
  text-decoration: none;
}

.header-link:hover {
  opacity: 0.9;
  transition: opacity 0.3s;
}

@media (max-width: 580px) {
  .header__title {
    font-size: 38px;
  }
}
</style>
