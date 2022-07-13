<script lang="ts" setup>

import {Gender, Popularity, Length, names} from '@/data'

interface OptionsState {
  gender: Gender;
  popularity: Popularity;
  length: Length;
}

import {reactive} from "vue"
const options = reactive<OptionsState>({
  gender: Gender.GIRL,
  popularity: Popularity.TRENDY,
  length: Length.LONG
})
const selectedNames = ref<string[]>([])

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
              :class="options.gender === Gender.BOY && 'option-active'"
              @click="options.gender = Gender.BOY"
              class="option option-left"
          >Boy</button>
          <button
              :class="options.gender === Gender.UNISEX && 'option-active'"
              @click="options.gender = Gender.UNISEX"
              class="option"
          >Unisex</button>
          <button
              :class="options.gender === Gender.GIRL && 'option-active'"
              @click="options.gender = Gender.GIRL"
              class="option option-right"
          >Girl</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose the names popularity</h4>
        <div class="option-buttons">
          <button
              :class="options.popularity === Popularity.TRENDY && 'option-active'"
              @click="options.popularity = Popularity.TRENDY"
              class="option option-left"
          >Trendy</button>
          <button
              :class="options.popularity === Popularity.UNIQUE && 'option-active'"
              @click="options.popularity = Popularity.UNIQUE"
              class="option option-right"
          >Unique</button>
        </div>
      </div>
      <div class="option-container">
        <h4>3) Choose names length</h4>
        <div class="option-buttons">
          <button
              :class="options.length === Length.LONG && 'option-active'"
              @click="options.length = Length.LONG"
              class="option option-left"
          >Long</button>
          <button
              :class="options.length === Length.ALL && 'option-active'"
              @click="options.length = Length.ALL"
              class="option"
          >All</button>
          <button
              :class="options.length === Length.SHORT && 'option-active'"
              @click="options.length = Length.SHORT"
              class="option option-right"
          >Short</button>
        </div>
      </div>
      <button
          class="primary"
      >Find Names</button>
    </div>
    {{ selectedNames }}
  </div>
</template>

<style scoped lang="scss">
.primary{
  background-color: yellowgreen;
  color:whitesmoke;
  border-radius: 6px;
  border: none;
  padding: 0.75rem 4rem;
  margin: 2rem 0 1rem;
  cursor: pointer;
  font-size: 23px;
}
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
    background-color: #9dcb1d;
    color: white;
  }
}

</style>


