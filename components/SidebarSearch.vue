<template>
  <div>
    <el-checkbox size="medium">Full Time</el-checkbox>
    <div style="margin-top: 1em">
      <h3><b>Location</b></h3>
      <el-input
        style="margin-top: 1em"
        placeholder="Ciudad, estado, zip code o Pais"
        prefix-icon="el-icon-location"
      ></el-input>
      <el-radio-group v-model="radioLocation">
        <el-radio :label="3" style="width: 100%; margin-top: 1em" size="medium"
          >Republica Dominicana</el-radio
        >
        <el-radio :label="6" style="width: 100%; margin-top: 1em" size="medium"
          >Colombia</el-radio
        >
        <el-radio :label="9" style="width: 100%; margin-top: 1em" size="medium"
          >Chile</el-radio
        >
      </el-radio-group>
    </div>
  </div>
</template>

<script>
export default {
  name: "SidebarSearch",
  data() {
    return {
      radioLocation: "",
    };
  },
};
</script>
