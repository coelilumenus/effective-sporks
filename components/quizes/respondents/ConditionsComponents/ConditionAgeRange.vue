<template>
  <div class="flex w-full justify-between items-center mb-8">
    <div class="w-full max-w-xs"><span class="bg-blue-200 py-1 px-2 rounded mr-2" v-if="index > 1">или</span> Диапазон {{ index }}</div>

    <div class="flex gap-x-4 w-full">
      <div class="flex items-center gap-x-2">
        от <el-input-number v-model="value.start" />
      </div>
      <div class="flex items-center gap-x-2">
        до <el-input-number v-model="value.end" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ConditionAgeRange',

  props: {
    value: {
      type: Object,
    },

    index: {
      type: Number,
    },
  },
}
</script>
