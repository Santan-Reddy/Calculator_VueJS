<script setup>
import {ref} from 'vue'
const baseUrl = ref('https://santan-reddy.github.io/Calculator_VueJS/')

const calculatorValue = ref(0)
const buttons = ref(["C","*","/","-",7,8,9,"+",4,5,6,"%",1,2,3,"=",0,"."])

function handleButton(value){
  if(value=="C"){
    calculatorValue.value = 0
  }
  else if(value=="="){
    calculatorValue.value = eval(calculatorValue.value)
  }
  else{
    calculatorValue.value += value
  }
}

</script>

<template>
  <div class="calculator">
    <div class="input">
      <!-- <input type="text" v-model="input">{{ calculatorValue || 0 }}</input> -->
      <div class="display">{{ calculatorValue || 0 }}</div>
    </div>
    <div class="buttons">
      <div class="nums"
      v-for="content in buttons" :key="number"
      >
        <button @click="handleButton(content)" class="button" :class="(content=='C' || content=='*' || content=='/' || content=='-' || content=='+' || content=='%' || content=='=')?'operator':'number'">{{content}}</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
*{
  margin: 0;padding: 0;box-sizing: border-box;
  font-family: 'Roboto', sans-serif;
}
.calculator{
  width: 60vw;
  margin: 0 auto;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #DAD7CD;
  border-radius: 1rem;
  .input{
    padding: 1rem;
    width: 50%;
    display: flex;
    /* justify-content: flex-end; */
    align-items: center;
    .display{
      width: 100%;
      background-color: #A3B18A;
      border-radius: 1rem;
      padding: 1rem;
      display: flex;
      justify-content: flex-end;
      align-items: center;
    }
  }
  .buttons{
    background-color: #A3B18A;
    padding: 1rem;
    width: 50%;
    border-radius: 1rem;
    display: grid;
    grid-template-columns: repeat(4,1fr);
    grid-template-rows: repeat(5,1fr);
    .nums{
      /* background-color: red; */
      display: flex;
      justify-content: center;
      align-items: center;
      margin: .2rem;
      .button{
        padding: 1rem;
        border: none;
        width: 100%;
        height: 100%;
        border-radius: 1rem;
        cursor: pointer;
        transition: background-color .3s ease;
      }
    }
  }
}
.operator{
  background-color: #3A5A40;
  color: white;
}
.operator:hover{
  background-color: #DAD7CD;
  color: black;
}
.number{
  background-color: #588157;
}
.number:hover{
  background-color: #DAD7CD;
}
</style>
