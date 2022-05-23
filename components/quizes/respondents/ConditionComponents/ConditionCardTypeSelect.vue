<template>
  <div class="flex w-full justify-between items-center mb-8">
    <div class="w-full max-w-xs"><span class="bg-blue-200 py-1 px-2 rounded mr-2" v-if="index > 1">или</span> Тип {{ index }}</div>

    <div class="flex gap-x-4 w-full">
      <div class="flex items-center gap-x-2">
        <el-select :value="value" @change="changeType">
          <el-option
            v-for="(option, i) in options"
            :key="option + i"
            :value="option"
            :label="option"
          />
        </el-select>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ConditionCardTypeSelect',
  
  data() {
    return {
      options: ['Активна', 'Не активна'],
    }
  },

  props: {
    value: {
      type: String,
    },

    index: {
      type: Number,
    },
  },
  
  methods: {
    changeType(type) {
      this.$emit('changeType', type, this.index - 1)
    }
  }
}
</script>
