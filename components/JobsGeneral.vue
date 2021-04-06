<template>
  <div class="w-100">

    <template v-if="loading === true">
      <b-row v-for="(item, index) in arrayLoading" :key="index" >
        <b-col cols="auto">
          <b-skeleton animation="wave" width="100%" style="border-radius: 4px" height="12vh"></b-skeleton
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
      >No hay mas ofertas de trabajos</b-alert
    >

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


      arrayLoading: [1,2,3]
    };
  },

  created() {
    this.getJobs(this.currentPage);
  },

  methods: {
    async getJobs(perPage) {
      this.jobsArray = "";
      try {
        const cors_api = "https://cors-anywhere-venky.herokuapp.com/";
        this.loading = true;
        const respuesta = await this.$axios.$get(
          `${cors_api}https://jobs.github.com/positions.json?&page=${perPage}`
        );

        this.loading = false;
        this.jobsArray = respuesta;
        console.log(respuesta);
      } catch (err) {}
    },
  },

  watch: {
    currentPage() {
      console.log("per page", this.currentPage);
      this.getJobs(this.currentPage);
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
