<template>
  <div class="tarjeta">
    <div class="tarjeta__image">
      <img
        class="image"
        :src="
          datos.item.company_logo === null
            ? 'https://gravatar.com/avatar/6c753164cd2239b9afbc23670a8e1de7?s=400&d=robohash&r=x'
            : datos.item.company_logo
        "
        :alt="datos.item.company"
        loading="lazy"
      />
    </div>
    <div class="tarjeta__info">
      <p class="m-0">
        <b>{{ datos.item.company }}</b>
      </p>
      <h5 style="font-size: 100%">{{ datos.item.title }}</h5>
      <el-tag size="medium"
        ><b> {{ datos.item.type }} </b></el-tag
      >
      <b-row align-h="end" align-v="center" class="pr-2">
        <b-col md="auto">
          <p style="font-size: 16px" class="m-0">
            <i class="el-icon-position mr-1"></i>{{ datos.item.location }}
          </p>
        </b-col>
        <b-col md="auto">
          <p style="font-size: 16px" class="m-0">
            <i class="el-icon-time mr-1"></i>5 day ayo
          </p>
        </b-col>
      </b-row>
    </div>
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
  min-height: 12vh;
  background: white;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.05);
  padding: 0 !important;
  display: flex;
  flex-direction: row;
}
.tarjeta__image {
  width: 20%;
  height: inherit;
  padding: 1em;
  display: flex;
  align-items: center;
  justify-content: center;
}
.tarjeta__image img {
  width: 100%;
  object-fit: contain;
}

.tarjeta__info {
  width: 80%;
  padding: 1em 0;
}

@media screen and (max-width:421px) {
  .tarjeta__image{
    width: 30%;
  }
  .tarjeta__info{
    width: 70%;
  }
}
</style>
