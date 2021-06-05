<template>
  <div class="calculator">
    <div class="calculator__display">{{ currentValue || 0 }}</div>
    <div @click="clear" class="calculator__btn">C</div>
    <div @click="sign" class="calculator__btn">+/-</div>
    <div @click="percent" class="calculator__btn">%</div>
    <div @click="divide" class="calculator__btn calculator__operator">/</div>
    <div @click="append('7')" class="calculator__btn">7</div>
    <div @click="append('8')" class="calculator__btn">8</div>
    <div @click="append('9')" class="calculator__btn">9</div>
    <div @click="times" class="calculator__btn calculator__operator">x</div>
    <div @click="append('4')" class="calculator__btn">4</div>
    <div @click="append('5')" class="calculator__btn">5</div>
    <div @click="append('6')" class="calculator__btn">6</div>
    <div @click="minus" class="calculator__btn calculator__operator">-</div>
    <div @click="append('1')" class="calculator__btn">1</div>
    <div @click="append('2')" class="calculator__btn">2</div>
    <div @click="append('3')" class="calculator__btn">3</div>
    <div @click="add" class="calculator__btn calculator__operator">+</div>
    <div @click="append('0')" class="calculator__btn calculator__zero">0</div>
    <div @click="dot" class="calculator__btn">.</div>
    <div @click="equal" class="calculator__btn calculator__operator">=</div>
  </div>
</template>

<script>
import { ref } from 'vue';
export default {
  setup() {
    let previous = ref(null);
    let currentValue = ref('');
    let operator = null;
    let operatorClicked = ref(false);

    function clear() {
      currentValue.value = '';
    }

    function sign() {
      currentValue.value =
        currentValue.value.charAt(0) === '-'
          ? currentValue.value.slice(1)
          : `-${currentValue.value}`;
    }

    function percent() {
      currentValue.value = `${parseFloat(currentValue.value) / 100}`;
    }

    function append(number) {
      if(operatorClicked.value) {
        currentValue.value = ''
        operatorClicked.value = false
      }

      currentValue.value = `${currentValue.value}${number}`;
    }

    function dot() {
      if (currentValue.value.indexOf('.') === -1) {
        append('.');
      }
    }

    function setprevious() {
      previous.value = currentValue.value;
      operatorClicked.value = true;
    }

    function divide() {
      operator = (a, b) => a / b;
      setprevious();
    }

    function times() {
      operator = (a, b) => a * b;
      setprevious();
    }

    function minus() {
      operator = (a, b) => a - b;
      setprevious();
    }

    function add() {
      operator = (a, b) => a + b;
      setprevious();
    }

    function equal() {
      currentValue.value = `${operator(parseFloat(previous.value), parseFloat(currentValue.value))}`
      previous.value = null
    }

    return {
      currentValue,
      clear,
      sign,
      percent,
      append,
      dot,
      divide,
      times,
      minus,
      add,
      equal
    };
  },
};
</script>

<style lang="scss" scoped>
.calculator {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  font-size: 2.5rem;
  text-align: center;
  width: 300px;
  color: #333;

  &__display {
    background: #333;
    color: white;
    padding: 1.5rem 0;
    grid-column: 1 / 5;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  &__zero {
    grid-column: 1 / 3;
  }

  &__btn {
    background-color: #eee;
    border: 1px solid #333;
    padding: 1rem 0;
    transition: all 300ms;
    cursor: pointer;

    &:hover {
      filter: sepia(60%);
    }
  }

  &__operator {
    background-color: orange;
    color: white;
  }
}
</style>
