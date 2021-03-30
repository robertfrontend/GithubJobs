<template>
  <div class="container">
    <Header />
    <div class="header-buscador">
      <el-row type="flex" justify="center" style="padding-top: 3.5em">
        <el-col :span="10">
          <el-input
            placeholder="Titulo, companies, expertise or benefits"
            prefix-icon="el-icon-s-cooperation"
          ></el-input>
        </el-col>
        <el-col :span="2"
          ><el-button type="primary" icon="el-icon-search">Buscar</el-button></el-col
        >
      </el-row>
    </div>
    <section class="seccionJobs">
      <el-row :gutter="20">
        <el-col :span="8" style="padding-right: 2em">
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
        </el-col>
        <el-col :span="16">1</el-col>
      </el-row>
    </section>
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
export default {
  components: {
    Header,
  },
  data() {
    return {
      radioLocation: "",
    };
  },
};
</script>

<style>
body {
  color: #2c3e50;
}
.container {
  margin: 0 5em;
}
.header-buscador {
  width: 100%;
  height: 15vh;
  margin-top: 3em;
  border-radius: 12px;
  background: url("../assets/backgroundImg.png");
  background-size: cover;
}
.seccionJobs {
  margin-top: 1em;
}
</style>
