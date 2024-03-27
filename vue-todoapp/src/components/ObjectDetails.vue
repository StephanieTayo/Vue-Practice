<script setup>
import { ref } from 'vue';

//const object = ref(null);
// Define prop for receiving object data from parent component
const props = defineProps({
  object: Object, 
});

</script>


<template>
  <div class="object-details">
    <h2>Object Details</h2>
    <div v-if="props.object">
      <p><strong>ID:</strong> {{ props.object.id }}</p>
      <p><strong>Name:</strong> {{ props.object.name }}</p>
      <!-- Display other properties as needed -->
    </div>
    <div v-else>
      <p>No object data available.</p>
    </div>
  </div>
</template>


<style scoped>
.object-details {
  margin-top: 20px;
}

.object-details h2 {
  margin-bottom: 10px;
}
</style>
