<template>
  <div class="result">
    <h2 class="result__title">Your ShortURL</h2>
    <input class="result__short-url" :value="shortUrl" />
    <button class="result__button" @click="onButtonClick">Copy</button>
    <p class="result__long-url">
      Original URL:
      <a :href="longUrl" class="result__long-url-link" target="_blank">{{
        longUrl
      }}</a>
    </p>
  </div>
</template>

<script>
export default {
  methods: {
    onButtonClick() {
      // copy shortUrl to clipboard
      navigator.clipboard.writeText(this.shortUrl);
    },
  },
  // computed property for short url
  computed: {
    shortUrl() {
      return "https://shrtnr.vercel.app/s/QWertY";
    },
    longUrl() {
      return "https://practicum.yandex.ru/trainer/vue-dev/lesson/cf0435ca-b9fb-412e-92b3-f78223f25b21/";
    },
  },
};
</script>

<style scoped>
.result {
  display: grid;
  padding-bottom: 90px;
  grid-template-areas:
    "title title"
    "short-url button"
    "long-url long-url";
  grid-template-columns: 1fr 187px;
  column-gap: 9px;
  row-gap: 26px;
}

.result__title {
  grid-area: title;
  text-align: center;
  font-size: 28px;
  font-weight: 400;
}

.result__short-url {
  grid-area: short-url;
  margin: 0;
  padding: 20px;
  font-size: 22px;
  font-weight: 400;
  border: 1px solid #8e8989;
  outline: none;
}

.result__button {
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

.result__button:hover {
  background-color: #2f80ed;
}
.result__long-url {
  grid-area: long-url;
  margin: 0;
  padding: 0;
  font-size: 22px;
  font-weight: 400;
}

.result__long-url-link {
  color: #2f80ed;
  text-decoration: none;
}
</style>
