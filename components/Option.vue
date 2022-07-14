<template>
  <div class="option-container">
    <h4>{{ option.title }}</h4>
    <div class="option-buttons">
      <button
          v-for="(value, index) in option.buttons"
          :key="value"
          :class="computeButtonClasses(value, index)"
          @click="options[option.category] = value"
          class="option"
      >
          {{ value }}
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">

import {Gender, Length, Popularity} from "~/data";

interface OptionProps {
  option: {
    title: string;
    category: string;
    buttons: Gender[] | Popularity[] | Length[]
  };
  options: {
    gender: Gender;
    popularity: Popularity;
    length: Length;
  }
}
const props = defineProps<OptionProps>()

const computeButtonClasses = (value, index) => {
  const classNames = [];
  if(props.options[props.option.category] === value) {
      classNames.push("option-active")
  }
  if(index === 0) classNames.push("option-left")
  if(index === props.option.buttons.length -1) classNames.push("option-right")
  return classNames.join(" ")
}
</script>

<style scoped>
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

</style>