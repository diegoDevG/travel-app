<template>
  <section class="destination">
    <h1>{{ destination.name }}</h1>
    <div class="destination details">
      <img
        :src="require(`@/assets/${destination.image}`)"
        :alt="destination.name"
      />
      <p>{{ destination.description }}</p>
    </div>
  </section>
</template>

<script>
import store from "@/store.js";

export default {
  computed: {
    destination() {
      return store.destinations.find(
        (destination) => destination.slug === this.$route.params.slug
      );
    },
  },
};
</script>
