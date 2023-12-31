<script setup lang="ts">
import { ref } from 'vue'
import { Icon } from '@iconify/vue'
import styles from './Select.module.scss'

const emit = defineEmits(['change'])

const opened = ref(false)
const itemSelected = ref('')

type Items = {
  name: string;
  value: string;
  icon?: string;
}

function handleChange(name: string, value: string) {
  itemSelected.value = name
  emit('change', value)
  opened.value = false
}

</script>

<template>
  <div :class="styles.selectContainer">
    <button
      :class="styles.button"
      @click="opened = !opened"
    >
      <span :class="styles.span">{{ itemSelected || label }}</span>
      <Icon icon="ph:caret-up-down" :class="styles.icon"/>
    </button>

    <ul
      :class="styles.list"
      v-if="opened"
    >
      <li
        :class="styles.listItem"
        v-for="(item, index) in items"
        :key="index"
      >
        <button
          :class="styles.itemButton"
          @click="handleChange(item.name, item.value)"
          type="button"
        >
          <Icon
            v-if="item.icon"
            :icon="item.icon"
          />

          <span :class="styles.itemName">
            {{ item.name }}
          </span>
        </button>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
export default {
  props: {
    label: String,
    items: Array<Items>,
  }
}
</script>