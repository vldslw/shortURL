<template>
  <form class="form">
    <h2 class="form__title">Shorten your link</h2>
    <input
      type="text"
      class="form__input form__input_link"
      placeholder="Enter your long link here"
      v-model="longUrl"
    />
    <p class="form__base-url">shrtnr.vercel.app/s/</p>
    <input
      type="text"
      class="form__input form__input_slug"
      placeholder="Customize link (optional)"
    />
    <button class="form__button" @click.prevent="onButtonClick">Shorten</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      longUrl: "",
    };
  },
  methods: {
    onButtonClick() {
      this.$router.push({
        path: "/shortened",
        query: { longUrl: this.longUrl },
      });
    },
  },
};
</script>

<style scoped>
.form {
  display: grid;
  grid-template-areas:
    "title title title"
    "input input input"
    "base-url slug button";
  grid-template-columns: 225px 1fr 187px;
  column-gap: 9px;
  row-gap: 26px;
}

.form__title {
  grid-area: title;
  text-align: center;
  font-size: 28px;
  font-weight: 400;
}

.form__input {
  padding: 20px;
  border: 1px solid #8e8989;
  background-color: #f5f5f5;
  font-size: 22px;
  font-weight: 400;
  outline: none;
}
.form__input_link {
  grid-area: input;
}

.form__input_slug {
  grid-area: slug;
}

.form__base-url {
  grid-area: base-url;
  margin: 0;
  padding: 20px;
  font-size: 22px;
  font-weight: 400;
}

.form__button {
  grid-area: button;
  padding: 17px 37px;
  color: #fff;
  background-color: black;
  font-size: 24px;
  font-weight: 400;
  line-height: normal;
  border: none;
  cursor: pointer;
}

.form__button:hover {
  background-color: #2f80ed;
}
</style>
