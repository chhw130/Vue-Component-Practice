<template>
  <li>
    <h2>{{ friends.name }}</h2>
    <button @click="toggleHandler()">Show Details</button>
  </li>
  <ul v-if="isToggle">
    <li><strong>Phone :</strong> {{ friends.phone }}</li>
    <li><strong>Email :</strong> {{ friends.email }}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      isToggle: false,
      friends: {
        id: "manuel",
        name: "Manuel Lorenz",
        email: "manuel@gmail.com",
        phone: "123-2134-3251",
      },
    };
  },

  methods: {
    toggleHandler() {
      this.isToggle = !this.isToggle;
    },
  },
};
</script>
