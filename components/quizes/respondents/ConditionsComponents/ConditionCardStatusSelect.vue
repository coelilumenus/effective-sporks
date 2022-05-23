<template>
  <div class="flex w-full justify-between items-center mb-8">
    <div class="w-full max-w-xs"><span class="bg-blue-200 py-1 px-2 rounded mr-2" v-if="index > 1">или</span> Статус {{ index }}</div>

    <div class="flex gap-x-4 w-full">
      <div class="flex items-center gap-x-2">
        <el-select :value="value" @change="changeStatus">
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
  name: 'ConditionCardStatusSelect',
  
  data() {
    return {
      options: ['Gold', 'Silver', 'Bronze'],
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
    changeStatus(status) {
      this.$emit('changeStatus', status, this.index - 1)
    }
  }
}
</script>
