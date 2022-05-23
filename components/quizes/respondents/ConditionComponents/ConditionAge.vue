<template>
  <div>
    <condition-age-range
      v-for="(range, i) in value.ranges"
      :key="'range' + i"
      v-model="value.ranges[i]"
      :index="i + 1"
    />

    <div class="flex w-full justify-between items-center">
      <div class="w-full max-w-xs"></div>

      <div class="flex w-full relative top-8">
        <el-button
          class="absolute"
          type="primary"
          plain
          icon="el-icon-plus"
          @click="onAddRange"
        >
          Добавить диапазон
        </el-button>
      </div>
    </div>
  </div>
</template>

<script>
import ConditionAgeRange from './ConditionAgeRange.vue'

export default {
  name: 'ConditionAge',

  components: {
    ConditionAgeRange,
  },

  model: {
    prop: 'value',
    event: 'change',
  },

  props: {
    value: {
      type: Object,
    },
  },

  data() {
    return {
      defaultData: {
        ranges: [
          {
            start: 0,
            end: 0,
          },
        ],
      },
    }
  },

  computed: {
    isDataCorrect() {
      if (!this.value.data) return false

      return Object.keys(this.value.data).every((property) => {
        return this.defaultData.hasOwnProperty(property)
      })
    },
  },

  created() {
    if (!this.isValueCorrect) {
      this.initDefaultData()
    }
  },

  methods: {
    initDefaultData() {
      this.$emit('initDefaultData', this.defaultData)
    },

    onAddRange() {
      this.value.ranges.push({
        start: 0,
        end: 0,
      })
    },
  },
}
</script>
