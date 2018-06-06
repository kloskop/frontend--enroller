<template>
   <div>
      
       <label>Zaloguj się emailem</label>
       <input type="email" v-model="email">
       <button @click="enter()">ZALOGUJ SIĘ</button>
   </div>
</template>

<script>
export default {
  data() {
    return {
      email: ""
    };
  },
  methods: {
    enter() {
      this.$emit("login", this.email);
    }
  }
};
</script>