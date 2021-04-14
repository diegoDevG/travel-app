<template>
  <div class="nav">
    <p>The travel app</p>
    <ul>
      <li>
        <router-link to="/"> Home </router-link>
      </li>
      <li v-for="destination in destinations" :key="destination.name">
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
.nav {
  display: flex;
  justify-content: center;
}

.nav {
  padding: 30px;
}

.nav a {
  font-weight: bold;
  color: #2c3e50;
}

.nav a.router-link-exact-active {
  color: #42b983;
}
</style>
