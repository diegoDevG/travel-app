<template>
  <div>
    <GoBack />
    <section class="destination">
      <h1 class="pt-6 text-gray-600 text-3xl font-bold">
        {{ destination.name }}
      </h1>
      <div class="flex flex-col lg:flex-row">
        <div>
          <img
            class="mx-auto"
            :src="require(`@/assets/${destination.image}`)"
            :alt="destination.name"
          />
        </div>
        <div class="flex-1 p-6 text-center leading-7 text-2xl md:text-left">
          <p>{{ destination.description }}</p>
        </div>
      </div>
    </section>
    <section class="experiences py-40">
      <h2 id="experience" class="pt-10 p-6 text-gray-600 text-3xl">
        Top experiences in <strong>{{ destination.name }}</strong>
      </h2>
      <div class="cards flex flex-wrap justify-center">
        <div
          v-for="experience in destination.experiences"
          :key="experience.slug"
          class="card relative"
        >
          <router-link
            :to="{
              name: 'experienceDetails',
              params: { experienceSlug: experience.slug },
              hash: '#experience',
            }"
          >
            <div
              class="h-40 rounded-2xl my-4 max-w-lg overflow-hidden filter brightness-90 sm:h-80 sm:rounded-none sm:m-0"
            >
              <img
                :src="require(`@/assets/${experience.image}`)"
                :alt="experience.name"
              />
            </div>
            <span
              class="text-gray-100 text-base absolute inset-0 flex justify-center text-2xl items-center font-extrabold"
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
import GoBack from "@/components/GoBack";

export default {
  components: {
    GoBack,
  },
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
