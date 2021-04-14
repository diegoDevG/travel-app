<template>
  <section>
    <h2>Experiences</h2>
    <h3>{{ experience.name }}</h3>
    <div>
      <img
        :src="require(`@/assets/${experience.image}`)"
        :alt="experience.name"
      />
      <p>{{ experience.description }}</p>
    </div>
  </section>
</template>

<script>
import store from "@/store.js";

export default {
  props: {
    slug: {
      type: String,
      required: true,
    },
    experienceSlug: {
      type: String,
      required: true,
    },
  },

  computed: {
    destination() {
      return store.destinations.find((d) => d.slug === this.slug);
    },
    experience() {
      return this.destination.experiences.find(
        (e) => e.slug === this.experienceSlug
      );
    },
  },
};
</script>
