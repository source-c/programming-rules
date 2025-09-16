---
description: Enforces best practices for Vue development, focusing on component architecture, template syntax, and reactivity patterns. Provides comprehensive guidelines for writing clean, efficient, and maintainable Vue applications.
globs: ["**/*.vue", "**/*.js", "**/*.ts"]
---

## Vue-Specific Rules

Cursor rules in Vue provide intelligent navigation and manipulation capabilities designed specifically for Vue development. These rules help you work more efficiently with Vue components, directives, and template syntax.

### Component Navigation

- Navigate between component definitions and their usages
- Jump to lifecycle hook declarations and methods
- Move between template sections and script blocks
- Quick access to component props and computed properties

### Smart Selection

- Select template blocks and expressions
- Expand selection to include directives and their arguments
- Smart component prop and event selection
- Select complete component definitions including all blocks

### Code Manipulation

- Quick component creation and refactoring
- Automated directive handling and optimization
- Computed property and watcher management
- Template structure manipulation

## Best Practices

- Use template-aware navigation for better code organization
- Leverage directive-specific cursor movements
- Utilize component-aware selection patterns
- Follow Vue component lifecycle patterns
- Implement proper Composition API patterns when applicable

## Examples

```vue
<!-- Navigate between component sections -->
<template>
  <div class="user-profile">
    <h1>{{ user.name }}</h1>
    <UserStats
      :stats="userStats"
      @update="handleUpdate"
    />
  </div>
</template>

<script>
export default {
  name: 'UserProfile',
  props: {
    user: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      userStats: null
    }
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },
  methods: {
    handleUpdate(stats) {
      this.userStats = stats
    }
  }
}
</script>

<!-- Composition API Example -->
<script setup>
import { ref, computed, onMounted } from 'vue'

const props = defineProps({
  userId: {
    type: String,
    required: true
  }
})

const user = ref(null)
const userStats = ref(null)

const fullName = computed(() => {
  if (!user.value) return ''
  return `${user.value.firstName} ${user.value.lastName}`
})

onMounted(async () => {
  user.value = await fetchUser(props.userId)
})

function handleUpdate(stats) {
  userStats.value = stats
}
</script>
``

## Configuration

Customize Vue-specific cursor rules in your settings:

```json
{
  "vue.cursorRules": {
    "componentNavigation": true,
    "smartSelection": true,
    "templateHandling": true,
    "compositionApiSupport": true,
    "directiveAwareness": true
  }
}
