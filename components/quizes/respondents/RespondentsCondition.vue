<template>
  <div 
    class="flex flex-col gap-y-8 py-4 px-8 relative"
    :class="{'bg-blue-50': isIndexEven, 'bg-green-50': !isIndexEven, 'border-b': !lastIndex}"
  >
    <div
      v-if="!lastIndex"
      class="absolute -bottom-3.5 z-50 px-3 py-1 rounded text-sm"
      :class="{'bg-blue-100': isIndexEven, 'bg-green-100': !isIndexEven}"
    >
      И
    </div>
    
    <div class="flex w-full justify-between items-center">
      <div 
        v-if="index" 
        class="flex min-w-max max-w-xs w-full font-bold" 
        :class="{'text-blue-500': isIndexEven, 'text-green-500': !isIndexEven}"
      >
        Условие {{ index }}
      </div>

      <div class="w-full">
        <!-- Тут можно было бы использовать vuex, дабы избежать this.$set(...), однако, в рамках задачи это не критично -->
        <el-select
          class="w-full min-w-max"
          :value="value.type"
          @change="onSetValueType"
        >
          <el-option
            v-for="(option, i) in options"
            :key="option.value + i"
            :value="option.value"
            :label="option.label"
          />
        </el-select>
      </div>
    </div>

    <div v-if="value.type.length">
      <component
        :is="'Condition' + value.type"
        v-model="value.data"
        @initDefaultData="setDefaultData"
      />
    </div>

    <div class="flex gap-x-60 w-full justify-between items-center">
      <div></div>

      <div>
        <div></div>

        <div class="self-end">
          <el-button
            type="danger"
            plain
            icon="el-icon-delete"
            @click="$emit('deleteCondition')"
          >
            Удалить условие
          </el-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ConditionAge from './ConditionComponents/ConditionAge.vue'
import ConditionCardStatus from './ConditionComponents/ConditionCardStatus.vue'
import ConditionCardType from './ConditionComponents/ConditionCardType.vue'

export default {
  name: 'RespondentsCondition',

  components: {
    ConditionAge,
    ConditionCardStatus,
    ConditionCardType,
  },

  props: {
    value: {
      type: Object,
    },

    index: {
      type: Number,
    },
    
    lastIndex: {
      type: Boolean,
      default: false
    }
  },

  data() {
    return {
      options: [
        {
          value: 'Age',
          label: 'Возраст респондента',
        },
        {
          value: 'CardType',
          label: 'Тип карты лояльности',
        },
        {
          value: 'CardStatus',
          label: 'Статус карты лояльности',
        },
      ],
    }
  },
  
  computed: {
    isIndexEven() {
      return (this.index % 2  === 0)
    }
  },

  methods: {
    clearValueData() {
      this.$set(this.value, 'data', {})
    },

    setDefaultData(data) {
      this.$set(this.value, 'data', data)
    },

    onSetValueType(type) {
      this.clearValueData()
      this.$set(this.value, 'type', type)
    },
  },
}
</script>
