<template>
  <b-container v-if="jobs">
    <b-row class="mt-4">
      <b-col md="3">
        <nuxt-link to="/"><i class="el-icon-back"></i> Back to search</nuxt-link>
        <div class="mt-4">
          <h6 style="color: #b9bdcf"><b>HOW TO APPLY</b></h6>
          <p style="font-size: 14px">
            Please email a copy of your resume and online portfolio to wes@kasisto.com &
            CC {{ jobs.how_to_apply.email }}
          </p>
        </div>
      </b-col>
      <b-col md="12" lg="9">
        <b-row>
          <b-col cols="auto">
            <h5 style="color: #334680; font-weight: bold">{{ jobs.title }}</h5>
          </b-col>
          <b-col cols="auto">
            <el-tag size="medium"
              ><b> {{ jobs.type }} </b></el-tag
            >
          </b-col>
          <b-col md="12">
            <p>{{ jobs.created_at }}</p>
          </b-col>
        </b-row>

        <b-row>
          <b-col md="1">
            <img :src="jobs.company_logo" width="60" alt="" />
          </b-col>
          <b-col md="auto">
            <p class="mt-2 mb-0">
              <b>{{ jobs.company }}</b>
            </p>
            <p class="" style="font-size: 14px; color: #b9bdcf">
              <i class="el-icon-position mr-1"></i><b>{{ jobs.location }}</b>
            </p>
          </b-col>
          <b-col md="12">
            <div id="descripcion">{{jobs.description}}</div>
          </b-col>
        </b-row>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  data() {
    return {
      loading: true,
      jobs: null,
    };
  },
  async created() {
    const cors_api = "https://cors-anywhere-venky.herokuapp.com/";
    const urlJob = this.$route.params;
    const url = `${cors_api}https://jobs.github.com/positions/${urlJob.jobs}.json?markdown=true`;

    const respuesta = await this.$axios.$get(url);

    this.jobs = respuesta;

    // let text = `${this.jobs.description}`;
    // console.log(document.getElementById("descripcion"));

    // document.getElementById('descripcion').innerHTML = text

    console.log(respuesta);
  },

  mounted() {},
};
</script>
