<template>
  <div class="tarjeta">
    <b-row align-v="stretch">
      <b-col cols="2">
        <img
          class="image mx-2"
          :src="
            datos.item.company_logo === null
              ? 'https://gravatar.com/avatar/6c753164cd2239b9afbc23670a8e1de7?s=400&d=robohash&r=x'
              : datos.item.company_logo
          "
          width="100px"
          height="100px"
          :alt="datos.item.company"
        />
      </b-col>
      <b-col cols="auto" class="mx-sm-2 mx-md-0">
        <div>
          <p class="m-0"><b>{{ datos.item.company }}</b></p>
          <h5 style="font-size: 100%"> {{ datos.item.title  }} </h5>
          <b-row class="mt-3">
            <b-col md="2">
              <el-tag size="medium"><b> {{ datos.item.type }} </b></el-tag>
            </b-col>
            <b-col md="10" >
              <b-row align-h="end" align-v="center">
                <b-col cols="auto">
                  <p style="font-size: 16px" class="m-0">
                    <i class="el-icon-position mr-1"></i>{{ datos.item.location }}
                  </p>
                </b-col>
                <b-col cols="auto">
                  <p style="font-size: 16px" class="m-0">
                    <i class="el-icon-time mr-1"></i>5 day ayo
                  </p>
                </b-col>
              </b-row>
            </b-col>
          </b-row>
        </div>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  name: "Tarjeta",
  props: {
    datos: Object,
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
  object-fit: contain;
  border-radius: 4px;
  width: 100%;
}
h4 {
  font-weight: 400;
}
</style>
