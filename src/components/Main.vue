<template>
  <main id="main-container">
    <h1>Mathificent</h1>
    <SelectInput :currentValue="operation" label="Operation"
      id="operation" v-model="operation" :options="operations" />
    <SelectInput :currentValue="maxNumber" label="Maximum Number"
      id="max-number" v-model="maxNumber" :options="numbers" />
    <PlayButton />
    <p>current operation: {{operation}}</p>
    <p>max number: {{maxNumber}}</p>
  </main>
</template>

<script>
  import SelectInput from './SelectInput';
  import PlayButton from './PlayButton';

  export default {
    name: 'Main',
    components: {
      SelectInput,
      PlayButton
    },
    data: function() {
      return {
        operations: [
          ['Addition', '+'],
          ['Subtraction', '-'],
          ['Multiplication', 'x'],
          ['Division', '/']
        ],
        operation: 'x',
        maxNumber: '15'
      }
    },
    computed: {  /*Creating an array of numbers that we use to populate the maximum number select input.*/
      numbers: function() {
        const numbers = []; /*each element of the numbers array is a 2-element array, containing the value*/
        for (let number = 2; number <= 100; number++) { /*and the text of the option in the dropdown*/
          numbers.push([number, number]); /*in this case, the value and text are the same: the number*/
        }
        return numbers;
      }
    }
  }
</script>

<style scoped>
  #main-container {
    margin: auto;
    width: 380px;
  }
</style>