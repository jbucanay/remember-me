<template>
  <v-app>
    <the-header></the-header>
    <v-main class="flex flex-col align-center">
      <base-card class="py-3">
      <template #buttons>
        <v-card-actions>
        <v-btn color="purple" rounded="0">Stored Resources</v-btn>
        <v-btn color="purple" class="bg-purple" variant="flat" rounded="0">Add resource</v-btn>
      </v-card-actions>
      </template>
      </base-card>
      <add-resource></add-resource>
      
    </v-main>
  </v-app>
</template>

<script>
import TheHeader from './components/TheHeader.vue'
import BaseCard from './components/BaseCard.vue';
import AddResource from './components/AddResource.vue';


export default {
  components: { TheHeader,BaseCard, AddResource},
  data(){
    return {
      on: false
    }
  }
}
  
</script>
<style scoped>


</style>