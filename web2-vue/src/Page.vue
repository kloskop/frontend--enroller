<template>
  <div>
    <div class="clearfix">
            <div class="float-left"><h2>Witaj {{username}}!</h2></div>
            <div class="float-right"><button class="button button-outline" @click="logout()">Wyloguj</button></div>
        </div>

        <meeting-page :username="username"></meeting-page>
  </div>
</template>

<script>
import MeetingPage from "./MeetingPage";
export default {
   components: {
    MeetingPage
  },
  props: ["username"],
  data() {
    return {};
  },
  methods: {
    logout() {
      this.$emit("logout");
    }
  },
 
};
</script>