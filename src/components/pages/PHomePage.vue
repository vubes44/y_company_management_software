<template>
  <OHomeOrganism :companyName="props.companyName" />
  <MLink href="y-company-management-software-info.com">
    <ALabel styleType="secondary" componentType="span" margin="0 6px">
      Dowiedz się więcej o y@</ALabel
    >
  </MLink>
  <MLink href="y-company-management-software-policy.com"
    ><ALabel styleType="secondary" componentType="span" margin="0 6px">
      Polityka prywatności</ALabel
    >
  </MLink>
</template>
<script setup lang="ts">
import OHomeOrganism from "../organisms/OHomeOrganism.vue";
import MLink from "../molecules/MLink.vue";
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
<style scoped lang="scss"></style>
