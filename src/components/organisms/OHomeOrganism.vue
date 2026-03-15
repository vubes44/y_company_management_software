<template>
  <div class="scope">
    <ALabel componentType="h1" styleType="apptitle" margin="60px 100px"
      >y@</ALabel
    >
    <!--<ALabel componentType="p" styleType="secondary" margin="20px 100px">
      Pierwszy solidny, prawdziwie przydatny frejmłork do sensownego zarządzania firmą.
      Bez bzdurnych dodatków, badziewi, ograniczeń, udziwnień, biurokracji i innych komunistycznych pierdół</ALabel
    >-->
    <ALabel componentType="h2" styleType="secondary" margin="20px 100px">
      {{ props.companyName }}</ALabel
    >
    <AButton type="account-option">Zaloguj się</AButton>
  </div>
</template>
<script setup lang="ts">
import AButton from "../atoms/AButton.vue";
import ALabel from "../atoms/ALabel.vue";

const props = withDefaults(
  defineProps<{
    companyName: string;
  }>(),
  {
    companyName: "Nazwa firmy",
  },
);
</script>
<style scoped lang="scss">
.scope {
  border: 1px solid #fff;
  border-radius: 10px;
  padding-bottom: 150px;
  padding-left: 300px;
  padding-right: 300px;
}
</style>
