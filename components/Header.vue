<template>
  <el-header>
    <el-row style="">
      <el-col :span="4">
        <h2><b>Github</b> <span>Jobs</span></h2>
      </el-col>
    </el-row>
  </el-header>
</template>

<script>
export default {
  name: "Header",
};
</script>
<style scoped>
.el-header {
    padding-top: 1em;
}
.el-header h2 {
    font-weight: bold;
}
.el-header  span {
    font-weight: 400;
}
</style>