<template>
    <table v-if="meetings.length > 0">
        <thead>
        	<h3>Zaplanowane zajęcia({{meetings.length}})</h3>
            <tr>
                <th>Nazwa spotkania</th>
                <th>Opis</th>
                <th>Uczestnicy</th>
                <th></th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="meeting in meetings" :key="meeting.name">
                <td width="10%">{{ meeting.name }}</td>
                <td width="20%">{{ meeting.description }}</td>
                <td>
                    <li v-for="participant in meeting.participants" :key="participant" style="list-style-type: circle">
                        {{participant}}
                    </li>
                </td>
                
                <td style="width: 500px">
        			<div class="clearfix">
          				<div class="float-right">
                			<button v-if="meeting.participants.indexOf(user) < 0" class="button button-outline" @click="join(meeting)">Zapisz się</button>
                			<button v-if="meeting.participants.length < 1" @click="remove(meeting)">Usuń puste spotkanie</button>
                			<button v-if="meeting.participants.indexOf(user) > -1" class="button button-outline" @click="disjoin(meeting)">Wypisz się</button>
                		</div>	
                	</div>
                </td>	
            </tr>
        </tbody>
    </table>
    
    <table v-else>
        Brak zaplanowanych spotkań.
    </table>
</template>

<script>
export default {
    props: ['meetings', 'user'],
    methods:{
      join(meeting){
          this.$emit('join',meeting);
      },
      disjoin(meeting){
          this.$emit('disjoin',meeting);
      },
      remove(meeting){
          this.$emit('remove',meeting);
      }, 
  }
};
</script>