<template>


    <table v-if="meetings.length > 0">
        
        <thead>
            Zajęcia(obecnie:{{meetings.length}})
            <tr>
                <th>Nazwa spotkania</th>
                <th>Opis</th>
                <th>Uczestnicy</th>
                <th></th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="meeting in meetings" :key="meeting.name" align="left">
                <td>{{ meeting.name }}</td>
                <td>{{ meeting.description }}</td>
                <td>
                    <li v-for="participant in meeting.participants" :key="participant" style="list-style-type: circle">
                        {{participant}}
                    </li>
                </td>
                    <td align="right"><button v-if="meeting.participants.indexOf(username)<0" class="button button-outline" @click="subscribe(meeting)">ZAPISZ SIĘ</button></td>
                    <td align="right"><button v-if="meeting.participants.indexOf(username)!==-1" class="button button-outline" @click="unsubscribe(meeting)">WYPISZ SIĘ</button></td>
                    <td align="right"><button v-if="meeting.participants.length==0" class="button" @click="removeMeeting(meeting)">USUŃ PUSTE SPOTKANIE</button></td>
            </tr>
        </tbody>
    </table>
    <table v-else>
        Brak zaplanowanych spotkań
    </table>

</template>

<script>
export default {
  props: ["meetings", "username"],
  methods:{
      subscribe(meeting){
          this.$emit('subscribe',meeting);
      },
      removeMeeting(meeting){
        this.$emit('removeMeeting',meeting);
      },
      unsubscribe(meeting){
          this.$emit('unsubscribe',meeting);
      },
  }
};
</script>


<style>
</style>