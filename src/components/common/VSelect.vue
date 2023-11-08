<script setup>
import { ref } from 'vue';

defineProps({
  selectOption: Array,
}); // props를 통해서 parents -> child로 보낼 때 반드시 필요

const emit = defineEmits(['onKeySelect']);
// 어떤 함수가 호출되는지 부모에게 알려줄 emits 배열
const key = ref('');
const onSelect = () => {
  console.log(key.value + '선택 !!');
  emit('onKeySelect', key.value); // 부모에게 onKeySelect와 value를 보냄.
};
</script>

<template>
  <select v-model="key" @change="onSelect" class="form-select form-select-sm ms-5 me-1 w-50" aria-label="검색조건">
    <option v-for="opt in selectOption" key="opt.value" :value="opt.value">
      {{ opt.text }}
    </option>
  </select>
</template>

<style scoped></style>
