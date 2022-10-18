<template>
  <FirstComponent :name="name" @pressed="pressed" />
</template>

<script setup>
import FirstComponent from "../VueScriptSetupStudying/components/FirstComponent.vue";

let name = "Lili";

function pressed() {
  alert("Hello From Pressed Function");
}
</script>
<style></style>
