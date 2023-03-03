<template>
  <v-container fill-height>
    <v-row justify="center">
      <v-col cols="5">
        <v-card>
          <v-card-title>
            <h1>Crear cuenta</h1>
          </v-card-title>
          <v-card-subtitle>
            Crea tu cuenta gratuitamente hasta el 30 de julio de 2023
          </v-card-subtitle>
          <v-card-text>
            <v-form>
              <v-row>
                <v-col>
                  <v-text-field label="Nombre" />
                </v-col>
                <v-col>
                  <v-text-field label="Apellido" />
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
                  <v-btn depressed color="primary"> Crear cuenta </v-btn>
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
}
</script>
