<template>
  <q-item>
    <q-checkbox :model-value="complete" />
    <q-item-section v-if="!isUpdate" @click="onToggleField">{{ text }}</q-item-section>
    <q-item-section v-else @blur.stop.prevent="onToggleField">
      <q-input :model-value="text" @input="($event: any) => $emit('input', $event)" />
    </q-item-section>
    <q-item-section avatar>
      <q-btn round color="negative" @click="$emit('delete-item')" icon="delete" />
    </q-item-section>
  </q-item>
</template>

<script setup lang="ts">
import { ref } from 'vue'

export interface ITodoItem {
  complete: boolean,
  text: string,
}

withDefaults(defineProps<ITodoItem>(), {
  complete: false,
  text: ''
})

const isUpdate = ref(false)
// const textUpdate = ref(props.text)

const onToggleField = () => {
  console.log('isUpdate.value: ', isUpdate.value)
  isUpdate.value = !isUpdate.value
}

</script>
