<script lang="ts" setup>

enum Gender {
  GIRL = 'Girl',
  BOY = 'Boy',
  UNISEX = 'Unisex'
}
enum Popularity {
  TRENDY = 'Trendy',
  UNIQUE = 'Unique'
}
enum nameLength {
  LONG = 'Long',
  ALL = 'All',
  SHORT = 'Short'
}

interface OptionsState {
  gender: Gender;
  popularity: Popularity;
  length: nameLength
}

const obj: OptionsState = {
  gender: Gender.GIRL,
  popularity: Popularity.TRENDY,
  length: nameLength.LONG
}

import {reactive} from "vue"
const options = reactive({
  gender: "Girl",
  popularity: "Trendy",
  length: "Long"
})
</script>

<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" button below</p>
    <div class="options-container">
      <div class="option-container">
        <h4>1) Choose a gender</h4>
        <div class="option-buttons">
          <button
              :class="options.gender === 'Boy' && 'option-active'"
              class="option option-left"
          >Boy</button>
          <button
              :class="options.gender === 'Unisex' && 'option-active'"
              class="option"
          >Unisex</button>
          <button
              :class="options.gender === 'Girl' && 'option-active'"
              class="option option-right"
          >Girl</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose the names popularity</h4>
        <div class="option-buttons">
          <button
              :class="options.popularity === 'Trendy' && 'option-active'"
              class="option option-left"
          >Trendy</button>
          <button
              :class="options.popularity === 'Unique' && 'option-active'"
              class="option option-right"
          >Unique</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose names length</h4>
        <div class="option-buttons">
          <button
              :class="options.length === 'Long' && 'option-active'"
              class="option option-left"
          >Long</button>
          <button
              :class="options.length === 'All' && 'option-active'"
              class="option"
          >All</button>
          <button
              :class="options.length === 'Short' && 'option-active'"
              class="option option-right"
          >Short</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.container{
  height: 1000px;
  background-color: rgba(126, 126, 127, 0.99);
  font-family: Arial, SansSerif ;
  color: rgb(27, 60, 138);
  max-width: 100rem;
  margin: 0 auto;
  text-align: center;
  h1{
    font-size: 3rem;
  }
  h4{
    font-size: 1.2rem;
  }
  .options-container{
    background-color: rgb(255, 238, 236);
    border-radius: 2rem;
    padding: 1rem;
    width: 70%;
    margin:0  auto;
  }
  .option{
    background-color: whitesmoke;
    outline: 0.15rem solid rosybrown;
    border: none;
    padding: 0.75rem;
    width: 12rem;
    font-size: 1.4rem;
    font-weight: bold;
    color: blue;
  }
  .option-left{
    border-radius: 1rem 0 0 1rem;
  }
  .option-right{
    border-radius: 0 1rem 1rem 0;
  }
  .option-active{
    background-color: darkred;
    color: white;
  }
}

</style>


