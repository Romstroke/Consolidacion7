<template>
     <v-app-bar
      app
      color="purple darken-3"
      dark
    >

    <v-app-bar-nav-icon></v-app-bar-nav-icon>
    <h1>Cursos AlfaWeb</h1>
    <v-spacer></v-spacer>
    <v-btn @click="redirectTo2"  class="mr-3">
      <v-icon dark>
          mdi-home
        </v-icon>
    </v-btn>
    <!-- <v-divider></v-divider> -->
    <v-btn @click="redirectTo">
        <v-icon dark>
          mdi-wrench
        </v-icon>
    </v-btn>  
    </v-app-bar>
</template>

<script>
export default {
    name: 'nav-comp',
    // props: {},
    data: function(){
        return {}
    },
    // computed: {},
    methods: {
        redirectTo(){
             if(this.$route.path== '/administracion'){
                alert('Ya estás en Administración.')
                 return
            }
            this.$router.push('/administracion')
        },
        redirectTo2(){
             if(this.$route.path== '/'){
                alert('Ya estás en Home.')
                 return
            }
            this.$router.push('/')
        }
    }
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>