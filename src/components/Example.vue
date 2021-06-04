<template>
  <div>
    <h1>Bem vindo {{ name }} {{ lastName }}</h1>
    <div>
      <h2>Contador</h2>
      <div>
        <button @click="decrement">-</button>
        <button @click="increment">+</button>
      </div>
      <span>{{ counter }}</span>
    </div>
  </div>
</template>

<script>
import  { ref, reactive, onMounted, watch, computed } from 'vue'
export default {
  props: {
    name: {
      type: String,
      required: true,
    },
    lastName: {
      type: String,
      required: true,
    },
  },
  setup(props) {
    let counter = ref(0);


    // let counter = reactive({
    //   value: 0
    // })


    const multiplicarValor = computed(() => counter.value * 2)
    const adicionaValor = computed(() => counter.value + 1)

    watch(counter, (newValue, oldValue) => {
      console.log(`O novo valor é ${newValue}`)
      console.log(`O valor antigo é ${oldValue}`)
      console.log(`Valor da computada de multiplicação ${multiplicarValor.value}`)
      console.log(`Valor da computada de adição ${adicionaValor.value}`)
    })


    function increment() {
      return counter.value ++
    }

    function decrement() {
      return counter.value --
    }

    onMounted(() => {
      console.log(`Hello ${props.name} ${props.lastName}`)
    })

    return {
      counter,
      increment,
      decrement,
    };
  },
};
</script>
