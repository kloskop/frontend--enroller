<template>
    <form @submit.prevent="addNewMeeting()">
            <h3>Dodaj nowe spotkanie</h3>
            <label>Nazwa</label>
            <input type="text" v-model="newMeeting.name" v-bind:class="{ 'is-valid': hasEmptyName }">
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>       
            <div class="clearfix">
                <div class="float-left">
                  <button>Dodaj</button>
                </div>
                <div class="float-left" v-if="hasEmptyName" style="color:red"> Spotkanie musi mieć nazwę</div>
            </div>
        </form>
</template>

<script>
export default {
  data() {
    return {
      newMeeting: {
        participants:[],
      },
      hasEmptyName: false
    };
  },
  methods: {
    addNewMeeting() {
      if (!this.newMeeting.name || this.newMeeting.name.length < 1) {
        this.hasEmptyName = true;
      } else {
        this.$emit("added", this.newMeeting);
        this.newMeeting = {};
      }
    }
  }
};
</script>