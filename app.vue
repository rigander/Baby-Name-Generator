<script lang="ts" setup>

import {Gender, Length, names, Popularity} from '@/data'
import {reactive, ref} from "vue"
import Option from "~/components/Option.vue";

interface OptionsState {
  gender: Gender;
  popularity: Popularity;
  length: Length;
}
const options = reactive<OptionsState>({
  gender: Gender.GIRL,
  popularity: Popularity.TRENDY,
  length: Length.LONG
})
const computeSelectedNames = () => {
  const filteredNames = names
      .filter((name) => name.gender === options.gender)
      .filter((name) => name.popularity === options.popularity)
      .filter((name) => {
        if(options.length === Length.ALL) return true
        else return name.length === options.length
      })

      selectedNames.value = filteredNames.map(name => name.name);

}
const selectedNames = ref<string[]>([]);

const removeName = (index: number) => {
  const filteredNames = [...selectedNames.value]
  filteredNames.splice(index,1)
  selectedNames.value = filteredNames
}

const optionsArray =[
  {
    title: "1) Choose a gender",
    category: "gender",
    buttons: [Gender.GIRL, Gender.BOY, Gender.UNISEX]
  },
  {
    title: "2) Choose the names popularity",
    category: "popularity",
    buttons: [Popularity.TRENDY, Popularity.UNIQUE]
  },
  {
    title: "3) Choose name's length",
    category: "length",
    buttons: [Length.LONG, Length.SHORT, Length.ALL]
  }
]

</script>

<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" button below</p>
    <div class="options-container">
      <Option
          v-for="option in optionsArray"
          :key="option.title"
          :option="option"
          :options="options"
      />
      </div>
      <button
          @click="computeSelectedNames"
          class="primary"
      >Find Names</button>
    <div class="cards-container">
    <CardName
        v-for="(name, index) in selectedNames"
        :key="name"
        :name="name"
        @remove="() => removeName(index)"
        :index="index"
    />
    </div>
  </div>
</template>

<style scoped lang="scss">
.cards-container{
  display: flex;
  margin-top: 3rem;
  flex-wrap: wrap;
  justify-content: space-around;
}

.card h4{
  margin: 0;
  padding: 0;
}


.result{
  font-size: 1.4rem;
  font-weight: bold;
  padding-top: 2rem;
  margin: 0 auto;
  height: 100px;
  width: 700px;
  border: none;
  border-radius:0 0 2rem 2rem;
  background-color: #fbeceb;
  display: flex;
  justify-content: center;
  align-items: center;
}
.founded-names{
  width: 500px;
  background-color: #dbd9da;
  border: 2px solid #2e7eb4;
  border-radius: 1rem;
  padding: 0.5rem;
}
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

}

</style>


