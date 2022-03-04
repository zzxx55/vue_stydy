<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="display">
      <input v-model.number="attribute1" />
      <input v-model.number="attribute2" />
      = {{ result }} {{ error }}
    </div>
    <div class="keybord">
      <button @click="addition(attribute1, attribute2)">+</button>
      <button @click="subtraction(attribute1, attribute2)">-</button>
      <button @click="multiplication(attribute1, attribute2)">*</button>
      <button @click="division(attribute1, attribute2)">/</button>
      <button @click="exponentiation(attribute1, attribute2)">**</button>
    </div>
  </div>
</template>



<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      attribute1: 0,
      attribute2: 0,
      result: 0,
      error: "",
    };
  },
  methods: {
    addition(at1, at2) {
      this.result = at1 + at2;
    },
    subtraction(at1, at2) {
      this.result = at1 - at2;
    },
    multiplication(at1, at2) {
      this.result = at1 * at2;
    },
    division(at1, at2) {
      if (at2 === 0) {
        this.error = "На ноль делить нельзя";
      } else {
        this.result = at1 / at2;
      }
    },
    exponentiation(at1, at2) {
      this.result = at1 ** at2;
    },
  },
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
