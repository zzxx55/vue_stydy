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
      <input type="checkbox" id="checkbox" v-model="checked" />
      <label for="checkbox">Отобразить экраную клавиатуру</label>
      <br />
      <button
        v-show="checked"
        v-for="operand in operands"
        v-bind:key="operand"
        @click="setOperand(operand)"
      >
        {{ operand }}
      </button>
      <button v-show="checked" @click="delet()">&#8592;</button>
      <br />
      <br />
      <input type="radio" id="one" value="op1" v-model="picked" />
      <label for="one">Операнд1</label>
      <br />
      <input type="radio" id="two" value="op2" v-model="picked" />
      <label for="two">Операнд2</label>
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
      operands: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
      attribute1: 0,
      attribute2: 0,
      result: 0,
      error: "",
      picked: 0,
      checked: false,
      operand: 0,
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
    setOperand(operand) {
      if (this.picked == "op1") {
        this.attribute1 = operand;
      } else if (this.picked == "op2") {
        this.attribute2 = operand;
      }
    },
    // delete() {
    //   if (this.picked == "op1") {
    //     this.attribute1 = this.attribute1.substr(0, this.attribute1.length - 1);
    //   } else if (this.picked == "op2") {
    //     this.attribute2 = this.attribute2.substr(0, this.attribute2.length - 1);
    //   }
    // },
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
