<template>
    <form @submit.prevent="addNewMeeting()">
            <h3>Dodaj nowe spotkanie</h3>
            <label>Nazwa</label>
            <input type="text" v-model="newMeeting.name">
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>
            <div class="clearfix">
                <div class="float-left">
            		<button>Dodaj</button>
            	</div>
            	<div class="float-left" v-if="isEmpty" style="color:red"> Spotkanie musi mieć nazwę!</div>
            </div>
    </form>
</template>

<script>
export default {
  data() {
      return {
          newMeeting: {},
          isEmpty: false
      };
  },
  methods: {
      addNewMeeting() {
      	if (!this.newMeeting.name || this.newMeeting.name.length == 0) {
      		this.isEmpty = true;
      	} else {
        	this.$emit('added', this.newMeeting);
        	this.newMeeting = {};
        }
      }
  }
}
</script>