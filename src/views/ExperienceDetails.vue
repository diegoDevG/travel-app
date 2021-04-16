<template>
  <section>
    <h2>Experiences</h2>
    <h3 class="pt-6 text-gray-600 text-2xl">{{ experience.name }}</h3>
    <div class="flex flex-col lg:flex-row">
      <div class="mx-auto">
        <img
          :src="require(`@/assets/${experience.image}`)"
          :alt="experience.name"
        />
      </div>
      <div
        class="flex-1 p-6 text-center leading-7 text-base md:text-left lg:pr-0"
      >
        <p>{{ experience.description }}</p>
      </div>
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
