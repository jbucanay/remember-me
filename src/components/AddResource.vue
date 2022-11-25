<template>
    <Teleport to="body">
     <v-snackbar v-model="showSnack" color="white">
    <p :class="getColor">{{ message }}</p>
    <template v-slot:actions>
          <v-btn
            color="red"
            variant="text"
            @click="showSnack = false"
          >
            Close
          </v-btn>
        </template>
   </v-snackbar>
</Teleport>
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
    BaseCard,
    },
    inject: ['data', 'changeComponent'],
    data() {
        return {
            title: '',
            description: '',
            link: '',
            showSnack: false,
            message: ''
        }
    },
    methods: {
        submitForm(){
            if(this.title !== '' || this.description !== '' || this.link !== ''){
                const inputVals = {
                title: this.title,
                description: this.description,
                link:this.link,
                id: Date.now()
                }

                this.data.push(inputVals)
                this.showSnack = true;
                this.message = 'Submited form successfully!'
                this.changeComponent('stored-resource');

            } else {
                this.message = 'Failed to submit form!'
                this.showSnack = true;
            }
        }
    },
    computed: {
        getColor(){
            return this.message == 'Failed to submit form!' ? 'text-red' : 'text-green'
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