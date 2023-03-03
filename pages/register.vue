<template>
  <v-container fill-height>
    <v-row justify="center">
      <v-col cols="5">
        <v-card>
          <v-card-title>
            <h1>{{ title }}</h1>
          </v-card-title>
          <v-card-subtitle>
            Crea tu cuenta gratuitamente hasta el 30 de julio de 2023
          </v-card-subtitle>
          <v-card-text>
            <v-form>
              <v-row>
                <v-col>
                  <v-text-field label="Nombre" v-model="account.name"/>
                </v-col>
                <v-col>
                  <v-text-field label="Apellido" v-model="account.lastName"/>
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <v-text-field label="Correo" />
                </v-col>
                <v-col>
                  <v-text-field label="Contraseña" />
                </v-col>
              </v-row>
              <v-row>
                <v-col cols="4">
                  <v-checkbox
                    depressed
                    color="primary"
                    label="Aceptar terminos y condiciones"
                  ></v-checkbox>
                </v-col>
              </v-row>
              <v-row justify="center" align-self="center">
                <v-col cols="4" >
                  <v-btn depressed color="primary" @click="createAccount"> Crear cuenta </v-btn>
                </v-col>
              </v-row>
            </v-form>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
<script lang="ts">
export default {
  layout: 'blank',
  data(){
    return{
      title:"Crear cuenta",
      account:{
        name:"",
        lastName:""
      }
    }
  },

  methods:{
    createAccount(){
      console.log(`Hello world ${this.account.name}`);
    }
  }
}
</script>
