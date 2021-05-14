<template>
  <div>
    <el-checkbox size="medium" v-model="fulltime">Full Time</el-checkbox>
    <div style="margin-top: 1em">
      <h3><b>Location</b></h3>
      <el-input
        style="margin-top: 1em"
        placeholder="Ciudad, estado, zip code o Pais"
        prefix-icon="el-icon-location"
        v-model="input_search"
      ></el-input>
      <el-button
        v-if="input_search != ''"
        type="primary"
        size="small"
        class="w-100 mt-2"
        @click="emitBuscar"
        >Search</el-button
      >
      <br />
      <el-radio-group v-model="radioLocation">
        <el-radio :label="'NewYork'" style="width: 100%; margin-top: 1em" size="medium"
          >New York</el-radio
        >
        <el-radio :label="'Boston'" style="width: 100%; margin-top: 1em" size="medium"
          >Boston</el-radio
        >
        <el-radio :label="'California'" style="width: 100%; margin-top: 1em" size="medium"
          >California</el-radio
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
      input_search: "",

      fulltime: false,
      radioLocation: "",
    };
  },

  methods: {
    filtrandoSide() {
      const objeto = {
        fullTime: this.fulltime,
        location: this.radioLocation,
      };
      this.$emit("buscarCiudades", objeto);
    },

    emitBuscar() {
      console.log(this.input_search.replace(/ /g, ""));
      const objeto = {
        location: this.input_search.replace(),
        fulltime: this.fulltime,
      };
      this.$emit("buscarCiudades", objeto);
    },
  },

  watch: {
    radioLocation() {
      this.filtrandoSide();
    },
    fulltime() {
      this.filtrandoSide();
    },

  },
};
</script>
