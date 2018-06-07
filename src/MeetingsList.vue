<template>
    <table v-if="meetings.length > 0">
        <thead>
        	<h3>Zaplanowane zajęcia({{meetings.length}})</h3>
            <tr>
                <th>Nazwa spotkania</th>
                <th>Opis</th>
                <th>Uczestnicy</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="meeting in meetings" :key="meeting.name">
                <td>{{ meeting.name }}</td>
                <td>{{ meeting.description }}</td>
                <td></td>
                <td class="float-right"><button>Usuń puste spotkanie</button></td>
                <td class="float-right"><button class="button button-outline">Zapisz się</button></td>
            </tr>
        </tbody>
    </table>
    <table v-else>
        Brak zaplanowanych spotkań.
    </table>
</template>

<script>
export default {
    props: ['meetings']
}
</script>