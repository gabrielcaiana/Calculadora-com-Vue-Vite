<template>
  <div class="calculator">
    <div class="calculator__display">335.23523</div>
    <div class="calculator__btn ">C</div>
    <div class="calculator__btn ">+</div>
    <div class="calculator__btn ">%</div>
    <div class="calculator__btn calculator__operator">-</div>
    <div class="calculator__btn">7</div>
    <div class="calculator__btn">8</div>
    <div class="calculator__btn">9</div>
    <div class="calculator__btn calculator__operator">x</div>
    <div class="calculator__btn">4</div>
    <div class="calculator__btn">5</div>
    <div class="calculator__btn">6</div>
    <div class="calculator__btn calculator__operator">-</div>
    <div class="calculator__btn">1</div>
    <div class="calculator__btn">2</div>
    <div class="calculator__btn">3</div>
    <div class="calculator__btn calculator__operator">+</div>
    <div class="calculator__btn calculator__zero">0</div>
    <div class="calculator__btn">.</div>
    <div class="calculator__btn calculator__operator">=</div>
  </div>
</template>

<script setup></script>

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
