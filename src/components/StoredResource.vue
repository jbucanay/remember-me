<template>
  <base-card
    v-for="item in data"
    :key="item.id"
    class="pb-2 grid grid-flow-col grid-cols-2"
  >
    <template #storedResource>
      <div class="col-span-4">
        <v-card-title>
          {{ item.title }}
        </v-card-title>
        <v-card-text>
          {{ item.description }}
        </v-card-text>
        <v-card-subtitle class="text-orange-800 font-semibold">
          <a :href="item.link" target="_blank">View resource</a>
        </v-card-subtitle>
      </div>
      <div>
        <v-btn
          variant="text"
          class="text-purple capitalize"
          @click="deleteMe(item.id)"
          >Delete</v-btn
        >
      </div>
    </template>
  </base-card>
</template>

<script>
import BaseCard from "./BaseCard.vue";
export default {
  components: {
    BaseCard,
  },
  inject: ["data"],
  methods: {
    deleteMe(id) {
      const found = this.data.findIndex((item) => item.id === id);
      this.data.splice(found, 1);
    },
  },
};
</script>
