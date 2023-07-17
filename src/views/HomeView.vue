<template>
  <v-container justify-content="center">
     <h1>Lista de Cursos</h1>
     <v-divider></v-divider>
    <v-row>  
      <v-col cols="12" md="4" v-for="(curso, index) in cursos" :key="index">
        <v-card width="400">
          <v-img height="200px" :src="curso.img">
            <v-card-title class="pink darken-1 mt-8">
              <p class="ml-3">{{ curso.nombre }}</p>
            </v-card-title>
          </v-img>

          <v-card-text>
            <div class="font-weight-bold ml-8 mb-2">Información</div>

            <v-timeline align-top dense>
              <v-timeline-item
              color="deep-purple lighten-1"
              >
                <div>
                  <div class="font-weight-normal">
                    <strong>Costo: {{ curso.costo }}</strong>
                  </div>
                  <div>Duración: {{ curso.duracion }}</div>
                </div>
              </v-timeline-item>
               <v-timeline-item
                color="green"
              >
                <div>
                  <div class="font-weight-normal">
                    <strong>Cupos: {{ curso.cupos }}</strong>
                  </div>
                  <div>Completado: {{ curso.completado }}</div>
                </div>
              </v-timeline-item>
               <v-timeline-item
               color="deep-purple lighten-1"
              >
                <div>
                  <div class="font-weight-normal">
                    <strong>Fecha de registro:</strong>
                  </div>
                  <div>{{ curso.fecha_registro }}</div>
                </div>
              </v-timeline-item>
                <v-timeline-item
                 color="green"
              >
                <div>
                  <div class="font-weight-normal">
                    <strong>Descripción:</strong>
                  </div>
                  <div>{{ curso.descripcion }}</div>
                </div>
              </v-timeline-item>
            </v-timeline>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { mapState } from "vuex";
export default {
  name: "Home-view",
  data: function () {
    return {
    };
  },
  computed: {
    ...mapState(["cursos"]),
  },
  components: {},
};
</script>
