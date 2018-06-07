<template>
    <div v-if="isCreating">
       <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
       <meetings-list :meetings="meetings"></meetings-list>
    </div>
    <div v-else>
    	<button @click="showCreatingNewMeeting()">Dodaj nowe spotkanie</button>
		<meetings-list :meetings="meetings"></meetings-list>
	</div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";

export default {
  components: {NewMeetingForm, MeetingsList},
  
  data() {
      return {
          meetings: [],
          isCreating: false
      };
  },
  methods: {
      addNewMeeting(meeting) {
      	  this.meetings.push(meeting);
      	  this.isCreating=false;
      },
      showCreatingNewMeeting() {
      	  this.isCreating = true;
      }
  }
}
</script>