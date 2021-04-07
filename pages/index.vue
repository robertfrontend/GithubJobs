<template>
  <div class="container">
    <div class="header-buscador">
      <b-row align-v="center" align-h="center" style="padding-top: 2.5em">
        <b-col md="6" class="my-2 my-md-0 mx-4 mx-md-0">
          <el-input
            placeholder="Titulo, companies, expertise or benefits"
            prefix-icon="el-icon-s-cooperation"
            v-model="inputSearch"
          ></el-input>
        </b-col>
        <b-col md="auto" class="my-2 my-md-0 mx-4 text-center mx-md-0">
          <el-button type="primary" icon="el-icon-search">Buscar</el-button>
        </b-col>
      </b-row>
    </div>
    <section class="seccionJobs">
      <b-row>
        <b-col lg="4">
          <SidebarSearch />
        </b-col>
        <b-col lg="8">
          <JobsGeneral />
        </b-col>
      </b-row>
    </section>
  </div>
</template>

<script>
import SidebarSearch from "@/components/SidebarSearch.vue";
import JobsGeneral from "@/components/JobsGeneral.vue";
export default {
  data() {
    return {
      inputSearch: "",
    };
  },

  components: {
    SidebarSearch,
    JobsGeneral,
  },
};
</script>

<style>
body {
  color: #2c3e50;
  background: #f6f7fb;
}

.header-buscador {
  width: 100%;
  height: 15vh;
  margin-top: 3em;
  border-radius: 12px;
  background: url("../assets/backgroundImg.png");
  background-size: cover;
}

@media screen and (max-width:749px) {
  .header-buscador {
    height: 25vh;
  }
}

.seccionJobs {
  margin-top: 2em;
}
</style>
