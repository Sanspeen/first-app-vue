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
                  <v-text-field label="Nombre" v-model="account.name" />
                </v-col>
                <v-col>
                  <v-text-field label="Apellido" v-model="account.lastName" />
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <v-text-field label="Correo" v-model="account.email" />
                </v-col>
                <v-col>
                  <v-text-field
                    label="Contraseña"
                    v-model="account.pass"
                    :append-icon="showPassword ? 'mdi-eye-off' : 'mdi-eye'"
                    :type="showPassword ? 'text' : 'password'"
                    @click:append="changeVisivilityPassword()"
                  />
                </v-col>
              </v-row>
              <v-row>
                <v-col cols="4">
                  <v-checkbox
                    depressed
                    color="primary"
                    label="Aceptar terminos y condiciones"
                    v-model="account.polity"
                  ></v-checkbox>
                </v-col>
              </v-row>
              <v-row justify="center" align-self="center">
                <v-col cols="4">
                  <v-btn depressed color="primary" @click="createAccount">
                    Crear cuenta
                  </v-btn>
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
  layout: 'default',
  data() {
    return {
      title: 'Crear cuenta',
      showPassword: false,
      account: {
        name: '',
        lastName: '',
        email: '',
        pass: '',
        polity: false,
      },
    }
  },

  methods: {
    createAccount() {
      const url: string = 'http://localhost:3001/accounts'
      this.$axios
        .$post(url, this.account)
        .then((response) => {
          console.log('Cuenta creada correctamente', response)
        })
        .catch((err) => {
          console.error('Ha ocurrido un error', err)
        })
        .finally(() => {
          this.account.email = ''
          this.account.name = ''
          this.account.pass = ''
          this.account.lastName = ''
          this.account.polity = false

          console.log('La creacion de la cuenta ha finalizado')
        })
    },
    changeVisivilityPassword() {
      this.showPassword = !this.showPassword
      console.log(this.showPassword)
    },
  },
}
</script>
