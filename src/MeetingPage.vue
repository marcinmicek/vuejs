<template>
    <div v-if="isCreating">
        <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
		<meetings-list :meetings="meetings"></meetings-list>
    </div>
       	
    <div v-else>
       <button @click="showMeetingCreationForm()">Dodaj nowe spotkanie</button>
	   <meetings-list :meetings="meetings" :user="user" @join="addParticipant($event)" @disjoin="removeParticipant($event)" @remove="deleteMeeting($event)"></meetings-list>
	</div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";

export default {
  props: ['user'],
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
      	  this.isCreating = false;
      },
      showMeetingCreationForm() {
      	  this.isCreating = true;
      },
      addParticipant(meeting){
          meeting.participants.push(this.user);
      },
      removeParticipant(meeting){ 
      	  let meetingIndex = this.meetings.indexOf(meeting)
      	  let patricipantIndex= meeting.participants.indexOf(this.user)
      	  meeting.participants.splice(patricipantIndex,1);
      },
      deleteMeeting(meeting){
      	let i = this.meetings.indexOf(meeting) 
      	this.meetings.splice(i,1);
      },
  }
};
</script>