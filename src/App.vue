<template>
  <section>
    <header>
      <h1>My Friends</h1>
    </header>
    <new-friend @add-contact="addContact"></new-friend>
    <ul>
      <friends-contact
        v-for="friend in friends"
        :key="friend.id"
        :name="friend.name"
        :email="friend.email"
        :phone="friend.phone"
        :favorite="friend.favorite"
        @toggle-favorite="toggleFavoriteStatusHandler"
        @delete-friend="deleteFriendHandler"
      />
    </ul>
  </section>
</template>

<script>
import NewFriend from "./components/NewFriend.vue";
export default {
  components: { NewFriend },
  data() {
    return {
      friends: [
        {
          id: "manuel",
          name: "Manuel Lorenz",
          email: "manuel@gmail.com",
          phone: "123-2134-3251",
          favorite: false,
        },
        {
          id: "juli",
          name: "Juli Jones",
          email: "Juli@gmail.com",
          phone: "123-2744-3251",
          favorite: true,
        },
      ],
    };
  },
  methods: {
    toggleFavoriteStatusHandler(friendName) {
      const identifyFriend = this.friends.find(
        (friend) => friend.name === friendName
      );

      identifyFriend.favorite = !identifyFriend.favorite;
    },
    addContact(enteredData) {
      const newFriendData = {
        id: new Date().toISOString(),
        name: enteredData.enteredName,
        phone: enteredData.enteredPhone,
        email: enteredData.enteredEmail,
        isFavorite: false,
      };
      this.friends.push(newFriendData);
    },
    deleteFriendHandler(friendName) {
      this.friends = this.friends.filter(
        (friend) => friend.name !== friendName
      );
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: "Jost", sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

li,
form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>
