<script setup>

import ObjectSearch from "../components/ObjectSearch.vue";
import ObjectDetails from "../components/ObjectDetails.vue";
import { ref } from "vue";

const fetchedObject = ref(null);

const receiveObjectData = (data) => {
  fetchedObject.value = data;
};


</script>


<template> 
<main>
  <div class="about">
<h1>Search Objects</h1>
    <ObjectSearch @object-fetched="receiveObjectData" />
    <ObjectDetails :object="fetchedObject" />
    
  </div>
</main>
</template>

<style>
main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 16px;

  h1 {
    margin-bottom: 16px;
    text-align: center;
  }
}

</style> 






