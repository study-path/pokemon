<template>
  <div class="about">
    <!-- <div>{{ $route.params.slug }}</div> -->
    <div
      v-if="pokemon"
      class="flex flex-col justify-center items-сenter border-indigo-600 rounded-md w-3/12 m-auto bg-purple-100 shadow-2xl"
    >
      <h3 class="text-2xl text-green-900 p-5 uppercase text-center">
        {{ pokemon.name }}
      </h3>
      <div class="flex justify-center">
        <img class="w-48" :src="pokemon.sprites.front_shiny" alt="" />
        <img class="w-48" :src="pokemon.sprites.back_shiny" alt="" />
      </div>

      <h3 class="text-yellow-600 text-center">Types</h3>
      <div v-for="(type, i) in pokemon.types" :key="i">
        <h5 class="text-blue-500 text-center pb-4">
          {{ type.type.name }}
        </h5>
      </div>
    </div>
  </div>
</template>
<script>
import { useRoute } from "vue-router";
import { reactive, toRefs } from "vue";
export default {
  setup() {
    const route = useRoute();

    const state = reactive({
      pokemon: null,
    });

    fetch(`https://pokeapi.co/api/v2/pokemon/${route.params.slug}/`)
      .then((res) => res.json())
      .then((data) => {
        console.log(data);
        state.pokemon = data;
      });
    return { ...toRefs(state) };
  },
};
</script>
