<template>
  <li>
    <h2>
      {{ name }}
      {{ favoriteCompute }}
    </h2>
    <button @click="toggleHandler()">Show Details</button>
    <button @click="toggleFavoriteHandler()">Toggle Favorite</button>
  </li>
  <ul v-if="isToggle">
    <li><strong>Phone :</strong> {{ phone }}</li>
    <li><strong>Email :</strong> {{ email }}</li>
  </ul>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
    },
    email: {
      type: String,
      required: true,
    },
    phone: {
      type: String,
      required: true,
    },
    favorite: {
      type: Boolean,
      required: false,
      default: false,
    },
  },

  data() {
    return {
      isToggle: false,
    };
  },

  computed: {
    favoriteCompute() {
      return this.favorite ? "(Favorite)" : null;
    },
  },

  methods: {
    toggleHandler() {
      this.isToggle = !this.isToggle;
    },
    toggleFavoriteHandler() {
      this.$emit("toggle-favorite", this.name);
    },
  },
};
</script>
