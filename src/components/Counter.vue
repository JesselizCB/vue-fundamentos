<template>
  <div>
    <h2>{{ customTitle }}</h2>
    <p>{{ counter }} <sup>2</sup> = {{ getSquareValue }}</p>
    <button @click="increase">+1</button>
    <button @click="decrease">-1</button>
  </div>
</template>

<script>
export default {
  // props: ["title"],
  props: {
    title: String,
    start: {
      type: Number,
      default: 101,
      validator(value) {
        return value > 100;
      },
    },
  },
  data() {
    return {
      counter: this.start,
    };
  },
  methods: {
    increase() {
      this.counter += 1;
    },

    decrease() {
      this.counter -= 1;
    },
  },
  computed: {
    getSquareValue() {
      return this.counter * this.counter;
    },
    customTitle() {
      // return this.title ? this.title : "Counter";
      return this.title || "Counter";
    },
  },
};
</script>
<style>
button {
  background-color: #64bb87;
  border-radius: 5px;
  border: solid 1px #fff;
  color: #fff;
  cursor: pointer;
  margin: 0 5px;
  padding: 5px 15px;
}

button:hover {
  background-color: #5aa67b;
  transition: 0.3s ease-in-out;
}
</style>
