<template>
  <div>
    <div class="clearfix">
      		<div class="float-left"><h2>Witaj {{ user }}!</h2></div>
	  		<div class="float-right"><button class="button button-outline" @click="logOut()">Wyloguj</button></div>
	</div>
	<meeting-page :user="user"></meeting-page>
  </div>
</template>

<script>
import MeetingPage from "./MeetingPage";

export default {
   components: {
    MeetingPage
  },
  props: ['user'],
  data() {
    return {};
  },
  methods: {
    logOut() {
      this.$emit("logOut");
    }
  },
 
};
</script>