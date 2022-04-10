<script>
export default {
  name: "TwootItem",
  props: {
    username: {
      type: String,
      required: true,
    },
    twoot: {
      type: Object,
      required: true,
    },
  },
  methods: {
    favTwoot(id) {
      this.$emit("favourite", id);
    },
  },
};
</script>
<template>
  <div class="twoot-item" @click="favTwoot(twoot.id)">
    <div>
      <div class="user-profile__twoot-user">@{{ username }}</div>
      <div class="user-profile__twoot-content">{{ twoot.content }}</div>
    </div>
  </div>
</template>

<style>
.twoot-item {
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid #dfe3e8;
  box-sizing: border-box;
  cursor: pointer;
  transition: all 0.25s ease;
  margin-left: auto;
  margin-bottom: 5px;
}

.twoot-item:hover {
  transform: scale(1.1, 1.1);
}

.user-profile__twoot-user {
  font-weight: bold;
}
</style>
