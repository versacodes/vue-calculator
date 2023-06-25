# Vue Guide

SFC(Single File Component)

```
	<script setup>
	import { ref } from 'vue'
	
	// component logic
	// declare some reactive state here.
	</script>
	
	<template>
	  <h1>Make me dynamic!</h1>
	</template>
``

#### reactive() - Proxies
`const counter = reactive({
	count: 0
})`

#### ref()
`const message = ref('Hello World!') `


message and counter can be accessed in template:

`
	<template>
		<h1>{{ message }}</h1>
		<p>{{ counter.count }}</p>
	</template>
`

`{{  }}` we can use any Javascript expression inside the double curly brackets	
