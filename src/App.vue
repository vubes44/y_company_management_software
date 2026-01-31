<template>
    <AButton @click="onClick">Test</AButton>

    <!-- submit -->
    <AButton type="submit" @click="onSubmit">Wyślij</AButton>

    <!-- account option -->
    <AButton type="account-option" @click="onAccount">Zaloguj się</AButton>

    <!-- disabled -->
    <AButton :is-disabled="true">Wyłączony</AButton>

    <!-- loading -->
    <AButton :is-loading="true">Ładowanie...</AButton>

    <!-- combined: disabled + loading (should be inert) -->
    <AButton :is-disabled="true" :is-loading="true">Nieaktywne</AButton>
</template>

<script setup lang="ts">
import AButton from './components/atoms/AButton.vue'

const onClick = (e: MouseEvent) => {
  console.log('Kliknięto: standard', e)
}

const onSubmit = (e: MouseEvent) => {
  console.log('Kliknięto: wyślij', e)
}

const onAccount = (e: MouseEvent) => {
  console.log('Kliknięto: opcje konta', e)
}
</script>

<style scoped>
</style>