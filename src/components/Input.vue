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
      :type="componentType"
      :class="styles.input"
      :value="modelValue"
      @input="emit('update:modelValue', ($event.target as HTMLInputElement).value)"
    >

    <button
      type="button"
      :class="styles.showBtn"
      v-if="type === 'password'"
      @click="componentType === 'password' ? componentType = 'text' : componentType = 'password'"
    >
      <Icon v-if="componentType === 'password'" icon="ph:eye" :class="styles.showIcon" />
      <Icon v-else icon="ph:eye-slash" :class="styles.hideIcon" />
    </button>
  </label>
</template>

<script lang="ts">
  export default {
    props: {
      icon: String,
      id: String,
      type: String,
      modelValue: String,
    },
    data() {
      return {
        componentType: this.type,
      }
    }
  }
</script>
