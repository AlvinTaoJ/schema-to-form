<template>
  <label :for="id" class="checkbox-label">
    <input :id="id" type="checkbox" :name="props.name" v-model="inputModel" class="checkbox">
    {{config.label}}
  </label>
</template>

<script setup>
import { computed } from "vue"
import { nanoid } from "nanoid";

const props = defineProps({
  name: String,
  config: Object,
  modelValue: Boolean
})
const emit = defineEmits(['update:modelValue'])

const inputModel = computed({
  get() {
    return props.modelValue
  },
  set(v) {
    emit('update:modelValue', v)
  }
})

const id = nanoid()

</script>

<style scoped lang="less">
.checkbox-label {
  margin: 20px 0;
  display: flex;
  align-items: center;
  cursor: pointer;
  font-size: 14px;
  font-weight: 500;
  color: #262626;
  .checkbox {
    width: 18px;
    height: 18px;
    margin-right: 5px;
  }
}
</style>