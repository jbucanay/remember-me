<template>
<base-card>
<template #addResource>
<v-card-text>
<form>
  <label for="title">Title</label><br>
  <input type="text" name="title"><br>
  <p><label for="Description">Description</label></p>
  <textarea name="Description" rows="3"></textarea>
  <br>
  <label for="link">Link</label><br>
  <input type="text" name="link">
  <v-btn flat class="bg-purple-900 text-white" rounded="0">Submit</v-btn>
</form> 
</v-card-text>
</template>
</base-card>

</template>


<script>
import BaseCard from './BaseCard.vue';

    export default {
  components: { BaseCard },
        component: {
            BaseCard
        }
    }
</script>

<style scoped>
input[type=text], textarea {
  width: 100%;
  padding: 3px;
  margin: 8px 0;
  box-sizing: border-box;
  border: 1px solid gray;
  border-radius: 3px;
}
label {
  font-weight: bolder;
}
</style>