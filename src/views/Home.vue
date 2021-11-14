<template>
  <div class="calculator">
    <span style="grid-area: num-0">{{ num1 }} {{ operators }}  {{ num2 }} <br/> {{result}}</span>
    <button @click="entry(1)" style="grid-area: num-1">1</button
    ><button @click="entry('2')" style="grid-area: num-2">2</button
    ><button @click="entry('3')" style="grid-area: num-3">3</button
    ><button @click="entry('4')" style="grid-area: num-4">4</button
    ><button @click="entry('5')" style="grid-area: num-5">5</button
    ><button @click="entry('6')" style="grid-area: num-6">6</button
    ><button @click="entry('7')" style="grid-area: num-7">7</button
    ><button @click="entry('8')" style="grid-area: num-8">8</button
    ><button @click="entry('9')" style="grid-area: num-9">9</button>
    <button @click="clear" style="grid-area: num-10">AC</button
    ><button style="grid-area: num-11">±</button
    ><button @click="operator('*')" style="grid-area: num-12">×</button
    ><button @click="operator('/')" style="grid-area: num-13">÷</button
    ><button @click="operator('+')" style="grid-area: num-14">+</button
    ><button @click="operator('-')" style="grid-area: num-15">-</button
    ><button @click="operator('.')" style="grid-area: num-16">.</button
    ><button @click="getResult" style="grid-area: num-17">=</button
    ><button @click="operator('%')" style="grid-area: num-18">%</button
    ><button @click="entry('0')" style="grid-area: num-19">0</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: "",
      num2: "",
      operators: "",
      result: "",
    };
  },
  methods: {
    entry(num) {
      // console.log(num);
      if(this.num1){
        this.num2 = num
      }else{
        this.num1 = num
      }
    },
    operator(operator){
      // console.log(operator);
      this.operators = operator
    },
    getResult(){
        let num1 = parseInt(this.num1)
        let num2 = parseInt(this.num2)
        this.result = this.operatorMap(this.operators,num1,num2)
    },
    operatorMap(operator,num1,num2){
      let operatorMap = {
        "+": num1 + num2,
        "-": num1 - num2,
        "*": num1 * num2,
        "/": num1 / num2,
        "%": num1 % num2,
      }
      return operatorMap[operator]
    },
    clear(){
      // 连续赋值为空
      this.num1 = this.num2 = this.operators = this.result = ""
    }
  },
};
</script>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(231, 231, 231);
}
.calculator {
  display: grid;
  grid-template-areas:
    "num-0 num-0 num-0 num-0"
    "num-10 num-11 num-18 num-13"
    "num-7 num-8 num-9 num-14"
    "num-4 num-5 num-6 num-15"
    "num-1 num-2 num-3 num-12"
    "num-19 num-16 num-17 num-17";
  grid-gap: 15px;
  grid-template-columns: repeat(4, 55px);
  grid-template-rows: repeat(6, 55px);
  box-shadow: -5px -5px 15px -5px white, 5px 5px 15px -5px rgba(0, 0, 0, 0.15);
  border-radius: 15px;
  padding: 25px;
}
.calculator {
  button {
  text-align: center;
  font-family: "fangsong";
  font-weight: bold;
  font-size: 22px;
  border: none;
  color: rgb(114, 114, 114);
  background-image: linear-gradient(135deg, rgba(0, 0, 0, 0.1), white);
  box-shadow: -2px -2px 8px -2px white, 2px 2px 8px -2px rgba(0, 0, 0, 0.15);
  border-radius: 20px;
}
}
.calculator {
  button:active {
  box-shadow: inset -2px -2px 8px -2px white,
    inset 2px 2px 8px -2px rgba(0, 0, 0, 0.15);
}
}
div {
  span {
  display: inline-block;
  color: rgb(70, 70, 70);
  padding: 0 8px 0 0;
  font-size: 25px;
  height: 100px;
  text-align: right;
  box-shadow: inset -2px -2px 10px -2px white,
    inset 2px 2px 10px -2px rgba(0, 0, 0, 0.15);
  overflow-x: auto;
}
}
</style>