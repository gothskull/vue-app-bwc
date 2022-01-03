<template>
  <b-card title="Create Awesome 🙌">
    <b-card-text>This is your second page.</b-card-text>
    <p
      v-for="{
        attributes: {
          id,
          nombre,
          fecha_ingreso,
          subdominio_pruebas,
          proveedor_hosting: {
            data: {
              attributes: { url, nombreHost },
            },
          },
        },
      } in proyectos.data"
      :key="id"
    >
      {{ nombre }} <br />
      {{ fecha_ingreso }} <br />
      {{ subdominio_pruebas }} <br />
      {{ url }} <br />
      el proveedor de hosting es {{ nombreHost }} <br />
    </p>
  </b-card>
</template>

<script>
import { BCard, BCardText } from "bootstrap-vue";
import { TMP_QUERY } from "@/queries/proyectos.js";

export default {
  data() {
    return {
      proyectos: [],
    };
  },
  apollo: {
    proyectos: {
      query: TMP_QUERY,
    },
  },
  components: {
    BCard,
    BCardText,
  },
};
</script>

<style></style>
