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
  computed: {
    longUrl() {
      return this.$route.query.longUrl;
    },
    shortUrl() {
      return this.$route.query.shortUrl;
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
  opacity: 0.8;
  transition: opacity 0.3s;
}

.result__button:active {
  opacity: 1;
  background-color: #2f80ed;
}
.result__long-url {
  grid-area: long-url;
  margin: 0;
  padding: 0;
  font-size: 22px;
  font-weight: 400;
  line-height: 32px;
}

.result__long-url-link {
  color: #2f80ed;
  text-decoration: none;
  display: block;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.result__long-url-link:hover {
  opacity: 0.9;
  transition: opacity 0.3s;
}

@media (max-width: 580px) {
  .result__short-url {
    font-size: 18px;
  }

  .result__long-url {
    font-size: 18px;
  }
  .result__title {
    font-size: 22px;
  }
  .result__button {
    font-size: 20px;
  }
}

@media (max-width: 530px) {
  .result {
    grid-template-areas:
      "title title"
      "short-url short-url"
      "button button"
      "long-url long-url";
    grid-template-columns: 1fr 1fr;
    row-gap: 13px;
  }
}
</style>
