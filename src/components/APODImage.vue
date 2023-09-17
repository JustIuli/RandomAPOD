<template>
  <div class="image">
    <img
        :src="info.url"
        :alt="info.title"
    />
  </div>
</template>

<script>
export default {
  props: {
    info: Object,
  },
};
</script>

<style scoped>
image {
  text-align: center;
}

image {
  max-width: 100%;
  height: auto;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}
</style>