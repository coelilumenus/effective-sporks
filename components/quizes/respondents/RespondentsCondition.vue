<template>
  <div class="flex max-w-5xl w-full justify-between items-center">
    <div>value.label</div>
    <div>
      <el-select>
        <el-option :key="'value.label' + '1'" label="Age" value="Возраст респондента"></el-option>
        <el-option :key="'value.label' + '2'" label="CardStatus" value="Тип карты лояльности"></el-option>
        <el-option :key="'value.label' + '3'" label="CardType" value="Статус карты лояльности"></el-option>
        <el-option :key="'value.label' + '4'" label="empty" value="Выберите условие"></el-option>
      </el-select>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RespondentsCondition',
  
  props: {
    value: {
      type: Object,
      default: () => {
        return {
          label: 'Условие',
          type: 'empty'
        }
      }
    }
  }
}
</script>
