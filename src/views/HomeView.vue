<template >
  <div>
    <h2>Home</h2>
    <input type="text" v-model="search">
    <p>Search Term - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">
    {{ name }}
    </div>
    <button @click="handleClick">Stop Watching</button>
  </div>
</template>
<script>
import { ref, computed, watch, watchEffect } from 'vue';

export default {
  name: 'Home',
  setup() {
    const search = ref('');
    const names = ref(['John', 'Joe', 'Jim']);

   const stopWatch = watch(search, () => {
      console.log("Watch search value changed");
    })

  const stopEffect =   watchEffect((() => {
      console.log("Watch effect search value changed", search.value);
    }))

    const matchingNames = computed(() => {
      return names.value.filter((name) => {
        return name.toLowerCase().includes(search.value.toLowerCase());
      });
    })

    const handleClick = () => {
      stopWatch();
      stopEffect();
    }

    return {names, search, matchingNames, handleClick}
  },
}
</script>
<style ></style>