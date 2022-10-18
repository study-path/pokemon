<template>
  <div class="p-14 flex justify-around">
    <router-link
      class="flex justify-center text-2xl text-yellow-600"
      to="/pokemonPicker"
      >Pokemon Picker</router-link
    >
    <router-link
      class="flex justify-center text-2xl text-yellow-600"
      to="/videoGameStore"
      >Video Game Store</router-link
    >
    <router-link
      class="flex justify-center text-2xl text-yellow-600"
      to="/vueScriptSetupStudying"
      >Vue Script Setup</router-link
    >
  </div>
  <router-view />
</template>
