<template>
  <div>
    <v-app>
    <v-card id="container" class="mx-auto my-auto">
      <v-card-title class="pb-0"> 
        <h1 class="mx-auto"> Jugueteria Otto Klaus Inicia Sesion</h1>
      </v-card-title>
      <v-card-text>
        <v-form>
          <v-text-field label="Ingresa tu correo"
          prepend-icon="mdi-account-circle"
          v-model='user'
          />
          <v-text-field label="Ingresa tu contraseña" :type="showPassword ? 'text' : 'password'"
          prepend-icon="mdi-lock"
          :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
          @click:append="showPassword = !showPassword"
          v-model='password'
          />
        </v-form>
      </v-card-text>
      <v-divider/>
      <v-card-actions>
        <v-btn block color="indigo" @click="login">Login</v-btn>
      </v-card-actions>
    </v-card>
  </v-app>
  </div>
</template>

<script>
import Firebase from 'firebase'
export default {
  name: 'App',

  data: () => ({
    user: '',
    password: '',
    showPassword: false
  }),
  methods: {
    login(){
      Firebase.auth().signInWithEmailAndPassword(this.user, this.password)
      .then(() =>{
        this.$router.push('/')
        alert(`Bienvenido ${this.user}`)
      }).catch(() =>{
        alert(`No Existes acá`)
      })
    }
  }
};
</script>
