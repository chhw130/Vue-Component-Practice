<template>
  <section>
    <h2>My Friends</h2>
    <ul>
      <friends-contact></friends-contact>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      friends: [
        {
          id: "manuel",
          name: "Manuel Lorenz",
          email: "manuel@gmail.com",
          phone: "123-2134-3251",
        },
        {
          id: "juli",
          name: "Juli Jones",
          email: "Juli@gmail.com",
          phone: "123-2744-3251",
        },
      ],
    };
  },
};
</script>
