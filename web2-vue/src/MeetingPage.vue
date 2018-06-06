<template>
    <div v-if="isAdding">
       <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
        <meetings-list :meetings="meetings"></meetings-list>
    </div>

    <div v-else>
      <button @click="enterAddingNewMeeting()">NOWE SPOTKANIE</button>
       <meetings-list :meetings="meetings" :username="username" @subscribe="addNewParticipant($event)" @removeMeeting="removeMeeting($event)" @unsubscribe="deleteParticipant($event)"></meetings-list>
    </div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";
export default {
  props: ["username"],
  components: { NewMeetingForm, MeetingsList },
  data() {
    return {
      meetings: [],
      isAdding: false
    };
  },
  methods: {
    addNewMeeting(meeting) {
      this.meetings.push(meeting);
      this.isAdding=false;
    },
    enterAddingNewMeeting() {
      this.isAdding = true;
    },
    addNewParticipant(meeting){
       meeting.participants.push(this.username);
    },
    removeMeeting(meeting){
      let i = this.meetings.indexOf(meeting) 
      this.meetings.splice(i,1);
    },
    deleteParticipant(meeting){ 
      let meetingIndex = this.meetings.indexOf(meeting)
      let patricipantIndex= meeting.participants.indexOf(this.username);
      meeting.participants.splice(patricipantIndex,1);
    },
  }
};
</script>