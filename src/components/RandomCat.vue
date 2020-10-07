<template>
  <div>
    <h1>{{ msg }}</h1>
    <form @submit.prevent="getCats">
      <div class="container form__input-container">
        <div class="row form-group">
          <div class="col-6 d-flex flex-column align-items-end">
            <label for="text">Titulo</label>
            <label for="text">Filtro</label>
            <label for="text">Color</label>
            <label for="text">Tamaño</label>
          </div>
          <div class="col-6 d-flex flex-column align-items-start">
            <input type="text" v-model="title" />
            <select v-model="filtro" name="" id="">
              <option disabled value="">Please select one</option>
              <option>bluur</option>
              <option>mono</option>
              <option>sepia</option>
              <option>negative</option>
              <option>paint</option>
              <option>pixel</option>
            </select>
            <div class="d-flex">
              <select v-model="color" name="" id="">
                <option disabled value="">Please select one</option>
                <option value="red">Rojo</option>
                <option value="blue">Azul</option>
                <option value="green">Verde</option>
                <option value="white">Blanco</option>
                <option value="yellow">Amarillo</option>
              </select>
              <div class="circle" :style="{ 'background-color': color }"></div>
            </div>
            <input type="number" v-model.number="size" />
          </div>
        </div>
      </div>
      <input
        type="submit"
        value="Obtener mi gatito"
        class="input_search--style"
        :disabled="loading"
      />
    </form>
    <div v-if="loading" class="spinner-border text-dark" role="status">
      <span class="sr-only">Loading...</span>
    </div>
    <img :src="image" alt="" />
  </div>
</template>

<script>
export default {
  name: "RandomCat",
  props: {
    msg: String,
  },
  data() {
    return {
      color: "",
      filtro: "",
      size: 0,
      image: "",
      title: "",
      loading: false,
    };
  },
  methods: {
    getCats() {
      this.loading = true;
      fetch(
        `https://cataas.com/cat/gif/says/${this.title}?filter=${this.filtro}&color=${this.color}&size=${this.size}`
      )
        .then((response) => response.url)
        .then((data) => {
          this.image = data;
          this.loading = false;
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  font-size: 4em;
  font-weight: 700;
  text-align: center;
  padding: 2em 0 1em;
}
.form__input-container {
  background-color: #f0aecf;
}
label {
  font-size: 30px;
  font-weight: bold;
  margin-top: 10px;
  color: #575555;
}
input {
  font-size: 30px;
  margin-bottom: 15px;
  border-radius: 50px;
}
select {
  font-size: 40px;
  margin-bottom: 5px;
  border-radius: 50px;
}
.input_search--style {
  margin-top: 10px;
  border-radius: 50px;
  color: #fff;
  background-color: #858282;
  padding: 10px;
}
.circle {
  height: 50px;
  width: 50px;
  border-radius: 50%;
  display: inline-block;
  margin-left: 1em;
}
</style>
