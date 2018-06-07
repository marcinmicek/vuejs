<template>
  <div id="app">
    <h1>Witaj w systemie do zapisów na zajęcia</h1>
    
    <div v-if="!authenticatedEmail">
      <login-form @login="logMeIn($event)"
      :button-label="'Zaloguj się'"></login-form>
    </div>

    <div v-else>
    	<div class="clearfix">
      		<div class="float-left"><h2>Witaj {{ authenticatedEmail }}!</h2></div>
	  		<div class="float-right"><button class="button button-outline" @click="logOut()">Wyloguj</button></div>
		</div>  		
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
    },
    addNewMeeting(meeting) {
    }
    
  }
}
</script>

<style lang="scss">

</style>
