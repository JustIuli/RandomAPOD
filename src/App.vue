<template>
  <div class="container">
    <APOD-image :info="info" />
    <APOD-details :info="info" />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20px;
  margin: 20px;
}

@media (max-width: 768px) {
  .container {
    flex-direction: column;
    text-align: center;
  }
}
</style>


<script>
import {ref, onMounted} from 'vue';
import axios from 'axios';
import APODImage from './components/APODImage.vue';
import APODDetails from './components/APODDetails.vue';

export default {
  components: {
    APODImage,
    APODDetails,
  },
  setup() {
    const info = ref({});
    const API_KEY = 'JgRtqhnRHzr4Zg04UnGj8S6tzFueD0fMw74fxYue'; // add your api key , you can get one at https://api.nasa.gov/index.html

    const generateRandomDate = (from) => {
      from = new Date(from);
      const randomTimestamp = from.getTime() + Math.random() * (new Date() - from);
      return new Date(randomTimestamp).toISOString().slice(0, 10);
    };

    const fetchData = () => {
      axios
          .get(`https://api.nasa.gov/planetary/apod?api_key=${API_KEY}&date=${generateRandomDate('2000-01-01')}`)
          .then((response) => {
            info.value = response.data;
          })
          .catch((error) => {
            console.error('Failed to fetch data', error);
          });
    };

    onMounted(() => {
      fetchData();
    });

    return {
      info,
    };
  },
};
</script>
