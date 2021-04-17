<template>
  <div
    class="flex pr-2 justify-between items-center p-3 font-bold text-3xl sticky top-0 border-b border-gray-300 bg-white h-28 z-10"
  >
    <router-link class="pr-3 text-purple-600 text-4xl" to="/">
      The Travel App
    </router-link>
    <ul class="hidden md:flex">
      <li class="pr-5">
        <router-link to="/"> Home </router-link>
      </li>
      <li
        class="pr-5"
        v-for="destination in destinations"
        :key="destination.name"
      >
        <router-link
          :to="{
            name: 'DestinationDetails',
            params: { slug: destination.slug },
          }"
        >
          {{ destination.name }}
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import store from "@/store";

export default {
  data() {
    return {
      destinations: store.destinations,
    };
  },
};
</script>

<style scoped>
.router-link-exact-active {
  color: #42b983;
}
</style>
