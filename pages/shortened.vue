<template>
  <div class="page">
    <Header />
    <main class="content">
      <Result />
      <router-link to="/" class="return-link">Shorten another URL</router-link>
    </main>
    <Footer />
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.page {
  margin: 0 auto;
}

.content {
  margin: 0 auto;
  padding: 120px 20px;
  max-width: 800px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.return-link {
  margin: 0 auto;
  color: #8e8989;
  font-size: 24px;
  font-weight: 400;
  text-decoration-line: underline;
  max-width: 300px;
}

.return-link:hover {
  opacity: 0.9;
  transition: opacity 0.3s;
}

@media (max-width: 580px) {
  .return-link {
    font-size: 20px;
  }
}
</style>
