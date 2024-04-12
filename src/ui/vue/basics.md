# Basics

## Vue Component

In most build-tool-enabled Vue projects, we author Vue components using an
HTML-like file format called Single-File Component, `.vue`. A Vue SFC consists
of three parts:

- `<template>`: the HTML template
- `<script>`: the JavaScript logic
- `<style>`: the CSS styles

```vue
<!-- https://vuejs.org/guide/introduction.html#single-file-components -->
<template>
  <button @click="count++">Count is: {{ count }}</button>
</template>

<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>

<style scoped>
button {
  font-weight: bold;
}
</style>
```

## Reactivity

Vue's reactivity is achieved by using the `ref` and `reactive` functions. `ref`
is used to create a reactive reference to a value, and `reactive` is used to
create a reactive object.

```vue
<!-- https://vuejs.org/tutorial/#step-2 -->
<template>
  <!-- Mustache for templating -->
  <h1>{{ message }}</h1>
  <p>Count is: {{ counter.count }}</p>
</template>

<script setup>
import { reactive, ref } from 'vue'

const counter = reactive({ count: 0 })
const message = ref('Hello World!')
</script>
```

Reactive properties can be computed using the `computed` function.

```vue
<template>
  <p>Count is: {{ count }}</p>
  <p>Double is: {{ doubleCount }}</p>
</template>

<script setup>
import { computed, ref } from 'vue'

const count = ref(0)
const doubleCount = computed(() => count.value * 2)
</script>
```

Reactive properties can be watched using the `watch` function.

```vue
<template>
  <p>Count is: {{ count }}</p>
</template>

<script setup>
import { ref, watch } from 'vue'

const count = ref(0)
watch(count, (newValue, oldValue) => {
  console.log(`count changed from ${oldValue} to ${newValue}`)
})
</script>
```

## V-Attributes

- `v-bind:attr = "expr"` (`:attr = "expr"`): binds an attribute to an expression
- `v-on:event = "handler"` (`@event = "handler"`): binds an event listener to a handler
- `v-model`: two-way binding for form input elements

```vue
<template>
  <p :class="active ? 'text-red-500' : 'text-black'">{{ text }}</p>
  <button @click="handler">click me</button>
  <input v-model="input" />
</template>

<script setup>
import { ref } from 'vue';
const active = ref(false);

function handler() {
  active.value = !active.value;
}

const text = ref('');
</script>
```

- `v-if="expr"`, `v-else-if="expr"`, `v-else`: conditional renders elements
- `v-show="expr"`: toggles the visibility of an element

```vue
<template>
  <div v-if="condA">Hello</div>
  <div v-else-if="condB">World</div>
  <div v-else>!</div>

  <div v-show="condC">Visible</div>
</template>

<script setup>
import { ref } from 'vue';

const condA = ref(false);
const condB = ref(false);
const condC = ref(false);
</script>
```

- `v-for="item in items"`, `v-for="(item, index) in items`: renders a list of items

```vue
<template>
  <ul>
    <li v-for="item in items" :key="item.id">{{ item.text }}</li>
  </ul>
</template>

<script setup>
import { ref } from 'vue';

const items = ref([
  { id: 1, text: 'Hello' },
  { id: 2, text: 'World' },
]);
</script>
```
