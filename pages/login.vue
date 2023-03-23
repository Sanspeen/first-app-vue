<template>
  <v-app id="inspire">
    <v-content>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar dark color="primary">
                <v-toolbar-title>Get started</v-toolbar-title>
              </v-toolbar>
              <v-card-text>
                <v-form>
                  <vs-alert variant="success" v-show="loginMessage">
                    Si tienes cuenta: Ingresado =D
                  </vs-alert>
                  <vs-alert variant="error" v-show="wrongAccountMessage">
                    Los datos no coinciden con alguna cuenta.
                  </vs-alert>
                  <v-text-field
                    prepend-icon="mdi-account"
                    name="login"
                    label="Email"
                    type="text"
                    v-model="account.email"
                  ></v-text-field>
                  <v-text-field
                    id="password"
                    prepend-icon="mdi-lock"
                    name="password"
                    label="Password"
                    v-model="account.pass"
                    :type="showPassword ? 'text' : 'password'"
                    :append-icon="showPassword ? 'mdi-eye-off' : 'mdi-eye'"
                    @click:append="changeVisivilityPassword()"
                  ></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary" @click="verifyIdentity">Let's go</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import VsAlert from '@vuesimple/vs-alert'

export default {
  layout: 'default',
  components: {
    VsAlert,
  },
  data() {
    return {
      accounts: [],
      showPassword: false,
      loginMessage: false,
      wrongAccountMessage: false,
      account: {
        email: '',
        pass: '',
      },
    }
  },
  methods: {
    changeVisivilityPassword() {
      this.showPassword = !this.showPassword
    },
    verifyIdentity() {
      const url = 'http://localhost:3001/accounts'
      this.$axios
        .$get(url)
        .then((response) => {
          const data = response
          this.accounts = data
        })
        .catch((err) => {
          console.log('Error consultando la API.', err)
        })
        .finally(() => {
          for (const element of this.accounts) {
            if (
              element.email === this.account.email &&
              element.pass === this.account.pass
            ) {
              this.loginMessage = true
              this.wrongAccountMessage = false  
            }

            if (this.loginMessage === false) {
              this.wrongAccountMessage = true
            }
          }
        })
    },
  },
}
</script>
