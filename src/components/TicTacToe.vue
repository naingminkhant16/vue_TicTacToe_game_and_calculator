<template>
  <p>First player will be O and Second will be X.</p>
  <div class="turn" v-if="!result">
    <div v-if="current == 'O'">O's turn</div>
    <div v-if="current == 'X'">X's turn</div>
  </div>
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
  <div v-if="result">
    <p>Game over</p>
    <p>{{ result }}</p>
  </div>
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
    let result = ref(null);
    let current = ref("O");
    let playGame = true;
    let execute = (block) => {
      if (playGame) {
        let value = document.querySelector(`#${block}`);
        block == "one" && one !== "O" && one !== "X"
          ? (one = current.value)
          : null;
        block == "two" ? (two = current.value) : null;
        block == "three" ? (three = current.value) : null;
        block == "four" ? (four = current.value) : null;
        block == "five" ? (five = current.value) : null;
        block == "six" ? (six = current.value) : null;
        block == "seven" ? (seven = current.value) : null;
        block == "eight" ? (eight = current.value) : null;
        block == "nine" ? (nine = current.value) : null;
        value.textContent = current.value;

        if (one == two && one == three) {
          result.value = `Winner - ${current.value}`;
          playGame = false;
        }
        if (one == four && one == seven) {
          result.value = `Winner - ${current.value}`;
          playGame = false;
        }
        if (one == five && one == nine) {
          result.value = `Winner - ${current.value}`;
          playGame = false;
        }
        if (four == five && four == six) {
          result.value = `Winner - ${current.value}`;
          playGame = false;
        }
        if (two == five && two == eight) {
          result.value = `Winner - ${current.value}`;
          playGame = false;
        }
        if (three == five && three == seven) {
          result.value = `Winner - ${current.value}`;
          playGame = false;
        }
        current.value == "O" ? (current.value = "X") : (current.value = "O");
      }
    };
    return { execute, result, current };
  },
};
</script>

<style>
.grid-container {
  display: grid;
  grid-template-columns: auto auto auto;
  /* padding: 8px; */
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
p {
  margin: 30px auto;
  font-size: 20px;
  font-weight: bolder;
}
.turn {
  width: 600px;
  margin: 20px auto;
  display: flex;
  align-items: center;
  justify-content: space-around;
  font-size: 16px;
  font-weight: bolder;
}
</style>