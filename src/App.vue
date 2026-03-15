<template>
  <PLoginPage :companyName="companyName" />
</template>

<script setup lang="ts">
import { ref } from "vue";
import PLoginPage from "./components/pages/PLoginPage.vue";

const companyName = ref("SofTDR");
</script>

<style scoped></style>
