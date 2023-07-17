<template>
  <v-container>
    <div class="justify-center">
      <h1>Administración</h1>
      <!-- MODAL AGREGAR CURSO -->
      <v-dialog v-model="dialog" width="800px">
        <template v-slot:activator="{ on, attrs }">
          <v-btn color="primary" dark v-bind="attrs" v-on="on">
            AGREGAR CURSO
          </v-btn>
        </template>
        <!-- FORMULARIO DENTRO DEL MODAL -->
        <v-card>
          <v-form ref="form" v-model="valid">
            <v-text-field
              v-model="name"
              :counter="10"
              :rules="nameRules"
              label="Nombre"
              required
            ></v-text-field>

            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="URL de la imagen"
              required
            ></v-text-field>

            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="Cupos del curso"
              required
            ></v-text-field>

            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="Inscritos en el curso"
              required
            ></v-text-field>

            <v-text-field
              v-model="name"
              :counter="10"
              :rules="nameRules"
              label="Duración del curso"
              required
            ></v-text-field>

            <v-text-field
              v-model="name"
              :counter="10"
              :rules="nameRules"
              label="Fecha de registro"
              required
            ></v-text-field>

            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="Costo del curso"
              required
            ></v-text-field>

            <v-textarea  color="teal">
              <template v-slot:label>
                <div>Descripción del curso</div>
              </template>
            </v-textarea>


            <v-btn
              :disabled="!valid"
              color="success"
              class="mr-4"
              @click="validate"
            >
             AGREGAR
            </v-btn>

            <v-btn color="error" class="mr-4" @click="reset">
              LIMPIAR FORMULARIO
            </v-btn>

            <v-btn color="warning" @click="resetValidation">
              CANCELAR
            </v-btn>
          </v-form>
        </v-card>
      </v-dialog>
    </div>
    <v-divider></v-divider>
    <!-- TABLA CON INFO -->
    <v-row>
      <v-col cols="12">
        <v-simple-table dark class="tabla">
          <template v-slot:default>
            <thead>
              <tr>
                <th class="text-left">Curso</th>
                <th class="text-left">Cupos</th>
                <th class="text-left">Inscritos</th>
                <th class="text-left">Duración</th>
                <th class="text-left">Costo</th>
                <th class="text-left">Terminado</th>
                <th class="text-left">Fecha</th>
                <th class="text-left">Acciones</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(curso, index) in cursos" :key="index">
                <td>{{ curso.nombre }}</td>
                <td>{{ curso.cupos }}</td>
                <td>{{ curso.inscritos }}</td>
                <td>{{ curso.duracion }}</td>
                <td>{{ curso.costo }}</td>
                <td>{{ curso.completado }}</td>
                <td>{{ curso.fecha_registro }}</td>
                <td>
                  <v-icon class="mr-10" color="orange">mdi-pencil</v-icon>
                  <v-icon color="red">mdi-delete</v-icon>
                </td>
              </tr>
            </tbody>
          </template>
        </v-simple-table>
        <v-divider class="mt-5 mb-5"></v-divider>
        <!-- ALERTAS -->
        <v-alert dense outlined color="purple" icon="mdi-account-multiple">
          Cantidad total de alumnos permitidos: <strong>190</strong> alumnos.
        </v-alert>
        <v-alert dense outlined color="blue" icon="mdi-account-check">
          Cantidad total de alumnos inscritos: <strong>103</strong> alumnos.
        </v-alert>
        <v-alert dense outlined color="red" icon="mdi-account-plus-outline">
          Cantidad total de cupos restantes: <strong>2</strong> alumnos.
        </v-alert>
        <v-alert dense outlined color="pink" icon="mdi-cancel">
          Cantidad de cursos terminados: <strong>2</strong> cursos.
        </v-alert>
        <v-alert dense outlined color="lime darken-3" icon="mdi-bell-ring">
          Cantidad total de cursos activos: <strong>4</strong> cursos.
        </v-alert>
        <v-alert dense outlined color="orange" icon="mdi-bell-ring">
          Cantidad total de cursos: <strong>6</strong> cursos.
        </v-alert>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { mapState } from "vuex";
export default {
  name: "admin-view",
  // props: {},
  data: function () {
    return {
      dialog: false,
      valid: true,
      name: "",
      nameRules: [
        (v) => !!v || "Name is required",
        (v) => (v && v.length <= 10) || "Name must be less than 10 characters",
      ],
      email: "",
      emailRules: [
        (v) => !!v || "E-mail is required",
        (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
      ],
      select: null,
      items: ["Item 1", "Item 2", "Item 3", "Item 4"],
      checkbox: false,
    };
  },

  computed: {
    ...mapState(["cursos"]),
  },
  methods: {
    validate() {
      this.$refs.form.validate();
    },
    reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    },
  },
  // watch: {},
  // components: {},
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
};
</script>

<style scoped>
</style>