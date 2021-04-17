<template>
  <span class="flex cursor-pointer">
    <button class="border-0" @click="goBack">go back</button>
  </span>
</template>

<script>
export default {
  methods: {
    goBack() {
      return this.$router.go(-1);
    },
  },
};
</script>
