<template>
  <div id="app" style="display:flex; flex-direction:column; justify-content: center; align-items: center">
    @{{user.username}} - {{fullName}}
    <br>
    <strong>Followers: {{followers}}</strong>
    <button style="width:100px" @click="followUser">Follow</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'Harry_Preston',
        firstName: 'Harry',
        lastName: 'Preston',
        email: 'harry@gmail.com',
        isAdmin: true
      }
    };
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    }
  },
  methods: {
    followUser() {
      this.followers++;
    }
  }
};
</script>
