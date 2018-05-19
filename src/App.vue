<template>
  <div id="app">
    <h1>Witaj w systemie do zapisów na zajęcia</h1>
    
    <div v-if="!authenticatedEmail">
      <login-form @login="logMeIn($event)"
      :button-label="'Wchodzę'"></login-form>
    </div>

    <div v-else>
      <h2>Witaj {{ authenticatedEmail }}!</h2>
      <b>
        <p>
          <a href @click="logOut()">Wyloguj</a>
        </p>
      </b>
    </div>

  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";

export default {
  components: {LoginForm},
  data () {
    return {
      authenticatedEmail: ''
    }
  },
  methods: {
    logMeIn(email) {
      this.authenticatedEmail = email;
    },
    logOut() {
      this.authenticatedEmail = '';
    }
    
  }
}
</script>

<style lang="scss">

</style>
