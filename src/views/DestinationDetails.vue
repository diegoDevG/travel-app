<template>
  <div>
    <section class="destination">
      <h1 class="pt-6 text-gray-600 text-2xl">{{ destination.name }}</h1>
      <div class="flex flex-col lg:flex-row">
        <div>
          <img
            class="mx-auto"
            :src="require(`@/assets/${destination.image}`)"
            :alt="destination.name"
          />
        </div>
        <div
          class="flex-1 p-6 text-center leading-7 text-base md:text-left lg:pr-0"
        >
          <p>{{ destination.description }}</p>
        </div>
      </div>
    </section>
    <section class="experiences">
      <h2 class="pt-6 text-gray-600 text-2xl">
        Top experiences in <strong>{{ destination.name }}</strong>
      </h2>
      <div class="cards flex">
        <div
          v-for="experience in destination.experiences"
          :key="experience.slug"
          class="pr-4 last:p-0 relative"
        >
          <router-link
            :to="{
              name: 'experienceDetails',
              params: { experienceSlug: experience.slug },
            }"
          >
            <div>
              <img
                :src="require(`@/assets/${experience.image}`)"
                :alt="experience.name"
              />
            </div>
            <span
              class="text-gray-100 text-base absolute inset-0 flex justify-center items-center font-extrabold"
              >{{ experience.name }}</span
            >
          </router-link>
        </div>
      </div>
      <router-view :key="$route.path" />
    </section>
  </div>
</template>

<script>
import store from "@/store.js";

export default {
  props: {
    slug: {
      type: String,
      required: true,
    },
  },
  computed: {
    destination() {
      return store.destinations.find(
        (destination) => destination.slug === this.$route.params.slug
      );
    },
  },
};
</script>
