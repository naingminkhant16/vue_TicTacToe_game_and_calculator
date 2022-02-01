<template>
  <div class="calculator">
    <div class="display">{{ current || 0 }}</div>
    <div class="btn" @click="clear">C</div>
    <div class="btn" @click="sign">+/-</div>
    <div class="btn" @click="percentage">%</div>
    <div class="btn operator" @click="divide">/</div>
    <div class="btn" @click="append('7')">7</div>
    <div class="btn" @click="append('8')">8</div>
    <div class="btn" @click="append('9')">9</div>
    <div class="btn operator" @click="times">x</div>
    <div class="btn" @click="append('4')">4</div>
    <div class="btn" @click="append('5')">5</div>
    <div class="btn" @click="append('6')">6</div>
    <div class="btn operator" @click="minus">-</div>
    <div class="btn" @click="append('1')">1</div>
    <div class="btn" @click="append('2')">2</div>
    <div class="btn" @click="append('3')">3</div>
    <div class="btn operator" @click="add">+</div>
    <div class="zero" @click="append('0')">0</div>
    <div class="btn" @click="dot">.</div>
    <div class="btn operator" @click="equal">=</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: "",
      firstNum: null,
      operator: null,
      operatorClicked: false,
    };
  },
  methods: {
    clear() {
      this.current = "";
    },
    sign() {
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `- ${this.current}`;
    },
    percentage() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = "";
        this.operatorClicked = false;
      }
      this.current = `${this.current + number}`;
    },
    dot() {
      if (this.current.indexOf(".") === -1) {
        this.append(".");
      }
    },
    add() {
      this.operator = (Fnum, Snum) => (this.current = Fnum + Snum);
      this.setFirstNum();
    },
    minus() {
      this.operator = (Fnum, Snum) => (this.current = Fnum - Snum);
      this.setFirstNum();
    },
    divide() {
      this.operator = (Fnum, Snum) => (this.current = Fnum / Snum);
      this.setFirstNum();
    },
    times() {
      this.operator = (Fnum, Snum) => (this.current = Fnum * Snum);
      this.setFirstNum();
    },
    setFirstNum() {
      this.firstNum = this.current;
      this.operatorClicked = true;
    },
    equal() {
      if (this.firstNum) {
        this.operator(parseFloat(this.firstNum), parseFloat(this.current));
        this.firstNum = "";
      }
    },
  },
};
</script>

<style>
.calculator {
  max-width: 400px;
  margin: 50px auto;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(60px, auto);
  font-size: 40px;
}
.display {
  background-color: #333;
  color: white;
  grid-column-start: 1;
  grid-column-end: 5;
}
.zero {
  grid-column: 1/3;
  background-color: darkgrey;
}
.btn {
  background-color: rgb(226, 226, 226);
  border: 1px solid rgb(187, 187, 187);
}
.operator {
  background-color: darkorange;
  color: white;
}
</style>