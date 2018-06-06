<template>
  <div id="app">
    <h1>Witaj w systemie do zapisów na zajęcia</h1>
    
    <div v-if="!authenticatedEmail">
      <login-form @login="logMeIn($event)"
      :button-label="'Zaloguj się'"></login-form>
    </div>

    <div v-else>
    	
      	<h2>Witaj {{ authenticatedEmail }}!</h2>
	  	<a href @click="logOut()">Wychodzę</a>
	  	<meeting-page @addMeeting="addNewMeeting($event)"></meeting-page>
    </div>

  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import MeetingPage from "./MeetingPage";

export default {
  components: {LoginForm, MeetingPage},
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
