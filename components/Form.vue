<template>
  <form class="form" @submit.prevent="onSubmit">
    <h2 class="form__title">Shorten your link</h2>
    <input
      class="form__input form__input_link"
      placeholder="Enter your long link here"
      v-model="longUrl"
      type="url"
      required
    />
    <p class="form__base-url">shrtnr.vercel.app/s/</p>
    <input
      type="text"
      class="form__input form__input_slug"
      placeholder="Customize link (optional)"
      v-model="slug"
      minLength="3"
      maxLength="8"
    />
    <button class="form__button">Shorten</button>
  </form>
</template>

<script>
// here we import nanoid to generate random slugs, but we would normally do it in the backend if we had one
import { nanoid } from "nanoid";

// here we import axios, but we won't actually use it, since we don't have a backend to handle the request at this time
import axios from "axios";

export default {
  data() {
    return {
      longUrl: "",
      slug: "",
      shortUrl: "",
    };
  },
  methods: {
    // this is example code, because there is no backend to handle the request at this time,
    // so I just did it to make the app look like it is working
    onSubmit() {
      if (this.slug === "") {
        // generate random slug if slug is empty
        this.slug = nanoid(8);
        this.shortUrl = `https://shrtnr.vercel.app/s/${this.slug}`;
      } else {
        // use slug if slug is not empty
        this.shortUrl = `https://shrtnr.vercel.app/s/${this.slug}`;
      }
      this.$router.push({
        // redirect to /shortened route with query params
        path: "/shortened",
        query: { longUrl: this.longUrl, shortUrl: this.shortUrl },
      });
    },
    // this is how the request should have looked like with backend active
    async onSubmitAsync() {
      try {
        const response = await axios.post(
          "https://shrtnr.vercel.app/api/shorten",
          {
            longUrl: this.longUrl,
            // generating random slug if slug is empty would be done in the backend instead of the frontend,
            // so here we would just pass the slug as it is, wheter it is empty or not
            slug: this.slug,
          },
        );
        // here we would get the shortUrl from the backend response
        this.shortUrl = response.data.shortUrl;
        // when we would redirect to /shortened route with query params just as we did in the example code
        this.$router.push({
          path: "/shortened",
          query: { longUrl: this.longUrl, shortUrl: this.shortUrl },
        });
      } catch (error) {
        console.log(error);
      }
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
