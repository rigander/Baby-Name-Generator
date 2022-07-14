<template>
  <div
      class="card">
    <h4>{{ name }}</h4>
    <p @click="removeName">x</p>
  </div>
</template>

<script setup lang="ts">
interface NameProps {
  name: string
}
const props = defineProps<NameProps>();

const emit = defineEmits(["remove"])

const removeName = () => {
  emit("remove", props.index)
}
</script>

<style scoped>
.card{
  display: flex;
  justify-content: space-around;
  background-color: rgba(27,60,138, 0.75);
  width: 18%;
  color: whitesmoke;
  padding: 1rem;
  margin-right: 0.5rem;
  margin-bottom: 1rem;
  font-size: 20px;
  border-radius: 2rem;
}
.card p{
  margin: 0;
  cursor: pointer;
}
</style>