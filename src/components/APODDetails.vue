<template>
  <div class="details">
    <h2 class="title">{{ info.title }}</h2>
    <p class="date">{{ info.date }}</p>
    <p class="explanation">{{ info.explanation }}</p>
    <a
        :href="info.hdurl"
        target="_blank"
        class="view-hd"
    >View original image website</a>
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
.details {
  flex: 1;
}

.title {
  font-size: 24px;
  margin: 0;
  color: white;
}

.date {
  font-size: 16px;
  color: white;
}

.explanation {
  font-size: 16px;
  color: white;
}

a {
  display: inline-block;
  margin-top: 10px;
  font-size: 16px;
  text-decoration: none;
  color: #007BFF;
}
</style>