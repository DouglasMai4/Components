<script setup lang="ts">
import { Icon } from '@iconify/vue'
import styles from './Input.module.scss'

const emit = defineEmits(['update:modelValue'])
</script>

<template>
  <label :for="id" :class="styles.label">
    <Icon :icon="icon || 'ph:pen'" :class="styles.icon" />

    <input
      :id="id"
      v-bind="$attrs"
      :type="type"
      :class="styles.input"
      :value="modelValue"
      @input="emit('update:modelValue', ($event.target as HTMLInputElement).value)"
    >
  </label>
</template>

<script lang="ts">
  export default {
    props: {
      icon: String,
      id: String,
      type: String,
      modelValue: String,
    }
  }
</script>