 
  <script setup> 
  import axios from "axios";
 import { ref, defineEmits} from "vue";

 const emit = defineEmits(["object-fetched"]);

 import TodoButton from "./TodoButton.vue"; 
 import ErrorMsg from "./ErrorMsg.vue";

 const searchId =ref(''); 
 const errorMessage = ref('');

 const fetchObject = async () => {
  try {
    // Make a GET request to the API
    const response = await axios.get(`https://api.restful-api.dev/objects/${searchId.value}`);
     // Emit event to send object data
    emit('object-fetched', response.data);
    // Log the response
    console.log(response.data);
    console.log( response.data.name);
    errorMessage.value = '';
    // Handle the response data here, you can update your UI accordingly
  } catch (error) {
    
    // Handle any errors
    console.error('Error fetching object:', error);
    errorMessage.value = 'An error occurred while fetching object data.';
  }
};


  </script>
  
  <template>
    <div class="object-search">
        <div class="input-wrap"  >
      <input type="text" v-model="searchId" placeholder="Enter object ID">
      <TodoButton @click="fetchObject">Search</TodoButton>
      </div>
      <div v-if="errorMessage" class="error-template">
      <ErrorMsg/>
    </div>
    </div>
  </template>
 
  
  <style lang=scss scoped>
 
  
  .input-wrap {
  display: flex;
  transition: 250ms ease;
  border: 2px solid #41b080;



  &.input-err {
    border-color: red;
  } 

  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }

  input {
    width: 100%;
    padding: 8px 6px;
    border: none;

    &:focus {
      outline: none;
    }
  }

}

.error-template {
  margin-top: 10px;
  color: red;
  font-weight: bold;
}

  </style>
  