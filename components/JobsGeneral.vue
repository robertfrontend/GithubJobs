<template>
  <div class="w-100">
    <template v-if="loading === true">
      <b-row v-for="(item, index) in arrayLoading" :key="index">
        <b-col cols="auto">
          <b-skeleton
            animation="wave"
            width="100%"
            style="border-radius: 4px"
            height="12vh"
          ></b-skeleton
        ></b-col>
        <b-col cols="10"
          ><b-skeleton animation="wave" width="100%" height="12vh"></b-skeleton
        ></b-col>
      </b-row>
    </template>

    <b-row>
      <b-col cols="12" v-for="item in jobsArray" :key="item.id" class="my-2">
        <NuxtLink :to="`jobs/${item.id}`"><Tarjeta :datos="{ item }" /></NuxtLink>
      </b-col>
    </b-row>

    <b-alert :show="jobsArray.length === 0 && loading != true"
      >No hay mas ofertas de trabajos
      <br />
    </b-alert>

    <div class="text-center" v-if="jobsArray.length === 0 && loading != true">
      <el-button type="primary" size="small" @click="getJobs('', 1, 'getTodo')">Restart</el-button>
    </div>

    <b-pagination
      class="mt-2"
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
      aria-controls="my-table"
    ></b-pagination>
  </div>
</template>

<script>
import Tarjeta from "./Tarjeta.vue";
export default {
  name: "JobsGeneral",

  data() {
    return {
      perPage: 1,
      currentPage: 1,
      rows: 10,

      jobsArray: "",
      loading: false,

      arrayLoading: [1, 2, 3],

      cors_api: "https://cors-anywhere-venky.herokuapp.com/",

      filtroSidebar: false,
    };
  },

  created() {
    this.getJobs("", this.currentPage, "getTodo");
  },

  methods: {
    async getJobs(dato, perPage, tipo) {
      this.loading = true;
      this.jobsArray = "";

      const url = "https://jobs.github.com/";

      // traemos todas las ofertas
      if (tipo === "getTodo") {
        console.log("Peticion 1");
        try {
          const respuesta = await this.$axios.$get(
            `${this.cors_api}https://jobs.github.com/positions.json?&page=${perPage}`
          );

          this.jobsArray = respuesta;
        } catch (err) {
          console.log(err, "error get normal");
        }
      }

      // filtrado por location y por fulltime
      else if (tipo === "filtroSidebar") {
        this.filtroSidebar = true;
        console.log("Peticion 2");

        try {
          const locationURL = `${url}positions.json?full_time=${dato.fullTime}&location=${dato.location}`;
          const respuesta = await this.$axios.$get(this.cors_api + locationURL);
          this.jobsArray = respuesta;
        } catch (error) {
          console.log(error, "error filtroSidebar");
        }
      }
      // filtrado por pagina y por location
      else if (tipo === "filtroSidebar" || this.filtroSidebar) {
        console.log("Peticion 3");
        // traer paginas del filtro de sidebar
        const locationURL = `${url}positions.json?full_time=${dato.fullTime}&location=${dato.location}${perPage}`;
        const respuesta = await this.$axios.$get(this.cors_api + locationURL);
        console.log(respuesta, "respuesta location + perpage");
        this.jobsArray = respuesta;
      }
      // filtro por pagina normal
      else {
        if (this.filtroSidebar) return;
        console.log("Peticion 4");
        const respuesta = await this.$axios.$get(
          `${this.cors_api}https://jobs.github.com/positions.json?&page=${perPage}`
        );

        this.jobsArray = respuesta;
      }
      
       if(tipo === 'page') {
         console.log('poor pagina');
      }

      this.loading = false;
    },

    filtroLocation(dato) {
      // console.log("para filtrar", dato);
      this.getJobs(dato, this.currentPage, "filtroSidebar");
    },
  },

  watch: {
    currentPage() {
      console.log("per page", this.currentPage);
      this.getJobs("", this.currentPage, "page");
    },
  },

  components: {
    Tarjeta,
  },
};
</script>
<style scoped>
.tarjeta {
  width: 100%;
  background: white;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
  padding: 10px 10px;
  color: #334680;
}
.image {
  object-fit: cover;
  border-radius: 4px;
}
h4 {
  font-weight: 400;
}
</style>
