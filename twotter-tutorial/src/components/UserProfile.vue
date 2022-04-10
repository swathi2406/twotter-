<script>
import TwootItem from "./TwootItem.vue";
export default {
  name: "UserProfile",
  components: { TwootItem },
  data() {
    return {
      twootTypes: [
        {
          value: "draft",
          name: "Draft",
        },
        {
          value: "draft",
          name: "Draft",
        },
      ],
      followers: 0,
      user: {
        id: 1,
        username: "_Swartz_p99",
        firstName: "Swathi",
        lastName: "Sriram",
        email: "swarek99@gmail.com",
        isAdmin: true,
        twoots: [
          { id: 1, content: "Hi, I just joined twoots" },
          { id: 2, content: " This is amazing!" },
        ],
      },
    };
  },
  watch: {
    followers(newFollowersCount, oldFollowersCount) {
      if (oldFollowersCount < newFollowersCount) {
        console.log(`${this.user.username} has gained a new follower`);
      }
      if (oldFollowersCount > newFollowersCount) {
        console.log(`${this.user.username} has lost a follower`);
      }
    },
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
  },
  methods: {
    followingUser() {
      this.followers++;
      return this.followingUser;
    },
    unFollowUser() {
      this.followers--;
      return this.followers;
    },
    toggleFavourite(id) {
      console.log(`favoured Tweet#${id}`);
    },
  },
  mounted() {
    this.followingUser();
  },
};
</script>

<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <h1 class="user-profile__username">@{{ user.username }}</h1>
      <div class="user-profile__admin" v-if="user.isAdmin">Admin</div>
      <div class="user-profile__follower-count">
        <strong>Followers:</strong> {{ followers }}
      </div>
      <form class="user-profile__create-twoot">
        <label for="newTwoot"><strong>New Twoot</strong></label>
        <textarea id="newTwoot" rows="4" />

        <div class="user-profile__Create-twoot-type">
          <label for="newTwootType"><strong>Type: </strong></label>
          <select id="newTwootType">
            <option :value="option.value"></option>
          </select>
        </div>
      </form>
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

<style>
.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  grid-gap: 50px;
  padding: 50px 5%;
}
.user-profile__user-panel {
  display: flex;
  flex-direction: column;
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid #dfe3e8;
}
h1 {
  margin: 0;
}
.user-profile__admin {
  background: rebeccapurple;
  color: white;
  border-radius: 5px;
  margin-right: auto;
  padding: 0 10px;
  font-weight: bold;
  margin-top: 5px;
  margin-bottom: 20px;
}

.user-profile__create-twoot {
  display: flex;
  flex-direction: column;
  border-top: 1px solid dfe3e8;
  padding-top: 20px;
}
</style>
