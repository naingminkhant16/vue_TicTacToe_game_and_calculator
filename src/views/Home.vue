<template>
  <nav>
    <a class="cal" @click="show = true">Calculator</a> |
    <a class="ttt" @click="show = false">Tic-Tac-Toe</a>
  </nav>
  <div v-if="show">
    <Calculator></Calculator>
  </div>
  <div v-if="!show">
    <TicTacToe></TicTacToe>
  </div>
</template>

<script>
import TicTacToe from "../components/TicTacToe";
import Calculator from "../components/Calculator";
// @ is an alias to /src

export default {
  name: "Home",
  components: {
    TicTacToe,
    Calculator,
  },
  data() {
    return {
      show: false,
    };
  },
};
</script>
<style scoped>
nav {
  margin-top: 40px;
  font-size: 20px;
}

</style>