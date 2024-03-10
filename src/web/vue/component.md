# Component

## Props

A child component can accept input from the parent via props.

```vue
<!-- https://vuejs.org/tutorial/#step-12 -->
<!-- Child.vue -->
<template>
  <h2>{{ msg || 'No props passed yet' }}</h2>
</template>
<script setup>
const props = defineProps({
  msg: String
})
</script>

<!-- Parent.vue -->
<template>
  <Child :msg="greeting" />
</template>
<script setup>
import { ref } from 'vue'
import Child from './Child.vue'

const greeting = ref('Hello from parent')
</script>
```

## Emits

A child component can emit events to the parent.

```vue
<!-- https://vuejs.org/tutorial/#step-13 -->
<!-- Child.vue -->
<template>
  <h2>Child component</h2>
</template>
<script setup>
const emit = defineEmits(['response'])

emit('response', 'hello from child')
</script>

<!-- Parent.vue -->
<template>
  <Child @response="(msg) => childMsg = msg" />
  <p>{{ childMsg }}</p>
</template>
<script setup>
import { ref } from 'vue'
import Child from './Child.vue'

const childMsg = ref('No child msg yet')
</script>
```

## Slots

A parent component can pass content to a child component via slots.

```vue
<!-- https://vuejs.org/tutorial/#step-14 -->
<!-- Child.vue -->
<template>
  <slot>Fallback content</slot>
</template>

<!-- Parent.vue -->
<template>
  <ChildComp>Message: {{ msg }}</ChildComp>
</template>
<script setup>
import { ref } from 'vue'
import ChildComp from './ChildComp.vue'

const msg = ref('from parent')
</script>
```
