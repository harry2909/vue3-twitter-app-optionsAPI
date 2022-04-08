<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <h1 class="user-profile__username">@{{ user.username }}</h1>
      <div class="user-profile__admin-badge" v-if="user.isAdmin">Admin</div>
      <div class="user-profile__follower-count">
        <strong>Followers: </strong> {{ followers }}
      </div>
    </div>
    <div class="user-profile__twoots-wrapper">
      <TwootItem
        v-for="twoot in user.twoots"
        :key="twoot.id"
        :username="user.username"
        :twoot="twoot"
        @favourite="toggleFavourite"
      />
    </div>
  </div>
</template>

<script>
import TwootItem from "./TwootItem.vue";

export default {
  name: "UserProfile",
  components: { TwootItem },
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: "Harry_Preston",
        firstName: "Harry",
        lastName: "Preston",
        email: "harry@gmail.com",
        isAdmin: true,
        twoots: [
          { id: 1, content: "This is a twoot." },
          { id: 2, content: "This is a different twood." },
        ],
      },
    };
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower!`);
      }
    },
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
  },
  methods: {
    followUser() {
      this.followers++;
    },
    toggleFavourite(id) {
        console.log(`Favourited Tweet ${id}`)
    }
  },
  mounted() {
    this.followUser();
  },
};
</script>
