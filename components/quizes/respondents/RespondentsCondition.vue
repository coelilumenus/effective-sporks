<template>
  <div class="flex max-w-lg justify-between items-center">
    <div>label</div>
    <div class="flex w-full">
      <el-select v-model="select">
        <el-option key="1" label="1" value="1"></el-option>
        <el-option key="2" label="2" value="2"></el-option>
        <el-option key="3" label="3" value="3"></el-option>
      </el-select>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RespondentsCondition',

  data() {
    return {
      select: '1'
    }
  }
}
</script>
