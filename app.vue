<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" button below</p>
    <div class="options-container">
      <div class="option-container">
        <h4>1) Choose a gender</h4>
        <div class="option-buttons">
          <button class="option option-left">Boy</button>
          <button class="option">Unisex</button>
          <button
              :class="options.gender === 'Girl' && 'option-active'"
              class="option option-right">Girl</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose the names popularity</h4>
        <div class="option-buttons">
          <button class="option option-left">Trendy</button>
          <button class="option option-right">Unique</button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose names length</h4>
        <div class="option-buttons">
          <button class="option option-left">Long</button>
          <button class="option" >All</button>
          <button class="option option-right" >Short</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
 const options = reactive({
   gender: "Girl",
   popularity: "Unique",
   length: "Short"
 })
</script>

<style scoped lang="scss">
.container{
  font-family: Arial, SansSerif ;
  color: rgb(27, 60, 138);
  max-width: 50rem;
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
    width: 95%;
    margin: 4rem 0  auto;
  }
  button:hover{
    background: rgb(2,0,36);
    background: linear-gradient(277deg, rgba(2,0,36,1) 0%, rgba(9,9,121,0.9489559164733179) 28%, rgba(0,212,255,1) 100%);
    color: yellow;
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
  button:active{
    background: rgb(2,0,36);
    background: linear-gradient(0deg, rgba(2,0,36,1) 0%, rgba(9,9,121,0.9489559164733179) 28%, rgba(0,212,255,1) 100%);
    color: yellow;
  }
  .option-active {
    background-color: rgb(247, 76, 80);
    color: white;
  }
}

</style>


