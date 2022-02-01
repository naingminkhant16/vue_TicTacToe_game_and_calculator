<template>
  <div class="grid-container">
    <div class="grid-item" @click="execute('one')" id="one"></div>
    <div class="grid-item" @click="execute('two')" id="two"></div>
    <div class="grid-item" @click="execute('three')" id="three"></div>
    <div class="grid-item" @click="execute('four')" id="four"></div>
    <div class="grid-item" @click="execute('five')" id="five"></div>
    <div class="grid-item" @click="execute('six')" id="six"></div>
    <div class="grid-item" @click="execute('seven')" id="seven"></div>
    <div class="grid-item" @click="execute('eight')" id="eight"></div>
    <div class="grid-item" @click="execute('nine')" id="nine"></div>
  </div>
  <div>{{}}</div>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  setup() {
    let one = "one";
    let two = "two";
    let three = "three";
    let four = "four";
    let five = "five";
    let six = "six";
    let seven = "seven";
    let eight = "eight";
    let nine = "nine";

    let current = "O";
    let execute = (block) => {
      let value = document.querySelector(`#${block}`);
      block == "one" ? (one = current) : null;
      block == "two" ? (two = current) : null;
      block == "three" ? (three = current) : null;
      block == "four" ? (four = current) : null;
      block == "five" ? (five = current) : null;
      block == "six" ? (six = current) : null;
      block == "seven" ? (seven = current) : null;
      block == "eight" ? (eight = current) : null;
      block == "nine" ? (nine = current) : null;
      value.textContent = current;

      if (one == two && one == three) console.log(`${current} win.`);
      if (one == four && one == seven) console.log(`${current} win.`);
      if (one == five && one == nine) console.log(`${current} win.`);
      if (four == five && four == six) console.log(`${current} win.`);
      if (two == five && two == eight) console.log(`${current} win.`);
      if (three == five && three == seven) console.log(`${current} win.`);
      current == "O" ? (current = "X") : (current = "O");
    };
    return { execute };
  },
};
</script>

<style>
.grid-container {
  display: grid;
  grid-template-columns: auto auto auto;
  padding: 10px;
  margin: 20px auto;
  width: 500px;
  height: 400px;
  /* background-color: black; */
}
.grid-item {
  background-color: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(0, 0, 0, 0.8);
  /* padding: 50px; */
  font-size: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>