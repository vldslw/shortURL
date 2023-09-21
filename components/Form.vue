<template>
  <form class="form">
    <h2 class="form__title">Shorten your long URL</h2>
    <input type="text" class="form__input form__input_link" placeholder="Enter your long link here" />
    <p class="form__base-url">shorturl.com/</p>
    <input type="text" class="form__input form__input_slug" placeholder="Customize (optional)" />
    <button class="form__button">Shorten</button>
  </form>
</template>

<script>
  export default {
    
  }
</script>

<style scoped>
.form {
  display: grid;
  grid-template-areas: 
    "title title title"
    "input input input"
    "base-url slug button";
  grid-template-rows: 1fr 1fr 1fr;
  grid-template-columns: 225px 1fr 187px;
  column-gap: 9px;
  row-gap: 26px;
}

.form__title {
  grid-area: title;
  text-align: center;
}

.form__input_link {
  grid-area: input;
}

.form__input_slug {
  grid-area: slug;
}

.form__base-url {
  grid-area: base-url;
}

.form__button {
  grid-area: button;
  cursor: pointer;
}

</style>