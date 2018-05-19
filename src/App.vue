<template>
  <div id="app">
    <h1>Witaj w systemie do zapisów na zajęcia</h1>
    
    <div v-if="!isAuthenticated">
      <label>Zaloguj się emailem</label>
      <input type="email" v-model="email">
      <button @click="logIn()">Wchodzę</button>
    </div>

    <div v-else>
      <h2>Witaj {{ email }}!</h2>
      <b>
        <p>
          <a href @click="logOut()">Wyloguj</a>
        </p>
      </b>
    </div>

  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      email: 'marcin.micek@gmail.com',
      isAuthenticated: false
    }
  },
  methods: {
    logIn() {
      this.isAuthenticated = true;
    },
    logOut() {
      this.isAuthenticated = false;
    }
  }
}


</script>

<style lang="scss">

</style>
