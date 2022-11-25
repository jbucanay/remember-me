<template>
<base-card>
<template #addResource>
<v-card-text>
<form @submit.prevent="submitForm">
  <label for="title">Title</label><br>
  <input type="text" name="title" v-model="title"><br>
  <p><label for="Description">Description</label></p>
  <textarea name="Description" rows="3" v-model="description"></textarea>
  <br>
  <label for="link">Link</label><br>
  <input type="text" name="link" v-model="link">
  <v-btn 
    flat 
    class="bg-purple-900 text-white" 
    rounded="0" 
    type="submit"
    >Submit</v-btn>
</form> 
</v-card-text>
</template>
</base-card>

</template>


<script>
import BaseCard from './BaseCard.vue';

    export default {
  components: { 
    BaseCard 
    },
    inject: ['data', 'changeComponent'],
    data() {
        return {
            title: '',
            description: '',
            link: '',
            showSnack: false
        }
    },
    methods: {
        submitForm(){
            const inputVals = {
                title: this.title,
                description: this.description,
                link:this.link,
                id: Date.now()
            }
            this.data.push(inputVals)
            this.changeComponent('stored-resource')
        }
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