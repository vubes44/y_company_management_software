<template>
	<div class="app-root">
		<h1>Przykładowe ASelect</h1>

		<section class="example">
			<ASelect v-model="selection1" :options="options" placeholder="Choose an option" name="select-default" />
			<p class="value">wybrano: {{ selection1 }}</p>
		</section>

		<section class="example">
			<ASelect v-model="selection2" styleType="datafield" :options="options" name="select-datafield" />
			<p class="value">wybrano: {{ selection2 }}</p>
		</section>

		<section class="example">
			<ASelect v-model="selection3" styleType="settings" :options="optionsWithDisabled" placeholder="Select (settings)" name="select-settings" />
			<p class="value">wybrano: {{ selection3 }}</p>
		</section>

		<section class="example">
			<ASelect :isDisabled="true" :options="options" name="select-disabled" />
			<p class="note">niedostępne</p>
		</section>
	</div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import ASelect from './components/atoms/ASelect.vue'

const options = [
	{ value: 'one', label: 'One' },
	{ value: 'two', label: 'Two' },
	{ value: 'three', label: 'Three' }
]

const optionsWithDisabled = [
	{ value: '', label: 'None', disabled: true },
	{ value: 'apple', label: 'Apple' },
	{ value: 'banana', label: 'Banana' }
]

const selection1 = ref<string | number | null>(null)
const selection2 = ref<string | number | null>('two')
const selection3 = ref<string | number | null>(null)
</script>

<style scoped>
.app-root {
	padding: 1.5rem;
	font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
}
.example {
	margin-bottom: 1.25rem;
}
.example h2 {
	margin: 0 0 0.5rem 0;
	font-size: 1rem;
}
.value, .note {
	margin-top: 0.45rem;
	color: #333;
	font-size: 0.95rem;
}
</style>