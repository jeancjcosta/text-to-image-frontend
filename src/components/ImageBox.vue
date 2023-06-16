<template>
  <div>
    <input class="form__input" v-model="message" placeholder="Type image description" /><br>
    <button class="button" @click="generateImageDiffusers">Generate</button><br>
    <div v-if="encodedImage" >
      <img
        :src="`data:image/png;base64,${encodedImage}`"
        alt="Image generated"
        contain
        height="500"
        width="500"/>
    </div>
  </div>
</template>

<script>
import axios from "axios"
export default {
  name: "ImageBox",
  data() {
    return {
      encodedImage: null,
      message: "",
      base_url:"http://localhost:8081/" //put the frontend url here
    }
  },
  methods: {
    generateImageDiffusers() {
      axios.get(this.base_url+"text-to-image", {
        params: {
          text: this.message,
          model: "diffusers"
        }
      }).then(response => {
        this.encodedImage = response.data.slice(3, -2)
      })
    }
  }
}
</script>

<style scoped>
.button {
  background-image: linear-gradient(#42A1EC, #0070C9);
  border: 1px solid #0f1010;
  border-radius: 4px;
  box-sizing: border-box;
  color: #FFFFFF;
  cursor: pointer;
  direction: ltr;
  display: inline;
  font-family: 'Roboto', sans-serif;
  font-size: 17px;
  font-weight: 400;
  letter-spacing: -.022em;
  line-height: 1.47059;
  min-width: 30px;
  overflow: visible;
  padding: 10px;
  text-align: center;
  vertical-align: baseline;
  touch-action: manipulation;
  white-space: nowrap;
  position: center;
  width: 200px;
  margin: 10px;
}

.button:disabled {
  cursor: default;
  opacity: .3;
}

.button:hover {
  background-image: linear-gradient(#51A9EE, #147BCD);
  border-color: #1482D0;
  text-decoration: none;
}

.button:active {
  background-image: linear-gradient(#3D94D9, #0067B9);
  border-color: #006DBC;
  outline: none;
}

.button:focus {
  box-shadow: rgba(131, 192, 253, 0.5) 0 0 0 3px;
  outline: none;
}

*,
*::after,
*::before {
  margin: 0;
  padding: 20px;
  box-sizing: inherit;
}

body {
  height: 100vh;
  width: 100%;
  background: #828787; /* fallback for old browsers */
  background: linear-gradient(to right, #e0e0e1, #b9bfc2, #595b5b);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  color: #fff;
}

.form__label {
  font-family: 'Roboto', sans-serif;
  font-size: 1.2rem;
  margin-left: 2rem;
  margin-top: 0.7rem;
  display: block;
  transition: all 0.3s;
  transform: translateY(0rem);
}

.form__input {
  color: #333;
  font-size: 1.2rem;
  margin: 0 auto;
  padding: 1.5rem 2rem;
  border-radius: 0.2rem;
  background-color: rgb(255, 255, 255);
  border: none;
  width: 40%;
  display: block;
  border: 0.1rem solid;
  transition: all 0.3s;
}

.form__input:placeholder-shown + .form__label {
  opacity: 0;
  visibility: hidden;
  -webkit-transform: translateY(-4rem);
  transform: translateY(-4rem);
}
.form__input::placeholder {
  text-align: center;
}

</style>