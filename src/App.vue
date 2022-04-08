<template>
  <div id="app">
    {{user.username}}
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
};
</script>
