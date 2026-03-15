<template>
  <div class="scope">
    <ALabel componentType="h2" styleType="secondary" margin="30px 100px"
      >Zaloguj się do firmy</ALabel
    >
    <ALabel componentType="h3" styleType="secondary" margin="30px 100px">{{
      props.companyName
    }}</ALabel>
    <MTextAndInput
      margin="30px 100px"
      layoutStyle="label-top"
      labelStyleType="secondary"
    >
      <template #label>Login</template>
      <template #input>
        <AInput name="login" placeholder="" />
      </template>
    </MTextAndInput>

    <MTextAndInput
      margin="30px 100px"
      layoutStyle="label-top"
      labelStyleType="secondary"
    >
      <template #label>Hasło</template>
      <template #input>
        <AInput inputType="password" name="password" placeholder="" />
      </template>
    </MTextAndInput>

    <AButton type="account-option">Zaloguj się</AButton>
  </div>
</template>
<script setup lang="ts">
import AButton from "../atoms/AButton.vue";
import ALabel from "../atoms/ALabel.vue";
import MTextAndInput from "../molecules/MTextAndInput.vue";
import AInput from "../atoms/AInput.vue";

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
