<template>
  <div>
    <h1 class="p-3 text-gray-600 text-3xl font-bold">All destinations</h1>
    <div class="flex flex-col items-center md:flex-row">
      <div
        class="p-3"
        v-for="destination in destinations"
        :key="destination.name"
      >
        <router-link
          :to="{
            name: 'DestinationDetails',
            params: { slug: destination.slug },
          }"
        >
          <h2 class="p-6 text-gray-600 text-3xl font-bold">
            {{ destination.name }}
          </h2>
        </router-link>
        <figure>
          <router-link
            :to="{
              name: 'DestinationDetails',
              params: { slug: destination.slug },
            }"
          >
            <img
              class="rounded"
              :src="require(`@/assets/${destination.image}`)"
              :alt="destination.name"
            />
          </router-link>
        </figure>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import store from "@/store.js";

export default {
  name: "Home",
  components: {},

  data() {
    return {
      destinations: store.destinations,
    };
  },
};
</script>
