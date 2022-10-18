<template>
  <div class="flex flex-col items-center">
    <div>It is the FirstComponent</div>
    <h5>Received name: {{ props.name }}</h5>
    <button
      class="border-zinc-600 p-2 rounded-md bg-yellow-400"
      type="button"
      @click="getAlert"
    >
      Press me
    </button>
  </div>
</template>

<script setup>
const props = defineProps({ name: String });
const emits = defineEmits(["pressed"]);

function getAlert() {
  emits("pressed");
}
</script>
