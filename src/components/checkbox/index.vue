<template>
  <a-checkbox-group type="button" v-model="myValue" :disabled="myOption.disabled">
    <a-checkbox :value="item[fieldNames.value]" v-for="(item, index) in dicData" :key="index">{{
      item[fieldNames.label]
    }}</a-checkbox>
  </a-checkbox-group>
</template>

<script setup lang="ts">
import { CheckboxGroup as ACheckboxGroup, checkbox as ACheckbox } from '@arco-design/web-vue'
import { withDefaults } from 'vue'
import useSelect from '../_hooks/use-select'

const props = withDefaults(
  defineProps<{
    option: any
    modelValue?: string | number | boolean
  }>(),
  {
    option: {}
  }
)
const emit = defineEmits<{
  (event: 'update:modelValue', val: string | number | boolean | undefined): void
  (event: 'update-form', val: any): void
  (event: 'change', val: string | number | boolean | undefined): void
}>()

const { dicData, myOption, fieldNames, myValue } = useSelect(props, emit)
</script>
