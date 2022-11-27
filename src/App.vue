<template>
  <v-app>
    <the-header></the-header>
    <v-main class="flex flex-col align-center">
      <base-card class="py-3">
        <template #buttons>
          <v-card-actions>
            <v-btn
              color="purple"
              rounded="0"
              :variant="setStoredResource"
              @click="changeComponent('stored-resource')"
              class="capitalize"
              >Stored Resources</v-btn
            >
            <v-btn
              color="purple"
              :variant="setAddResource"
              rounded="0"
              @click="changeComponent('add-resource')"
              class="capitalize"
              >Add resource</v-btn
            >
          </v-card-actions>
        </template>
      </base-card>
      <keep-alive>
        <component :is="activeComp"></component>
      </keep-alive>
    </v-main>
  </v-app>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import BaseCard from "./components/BaseCard.vue";
import AddResource from "./components/AddResource.vue";
import StoredResource from "./components/StoredResource.vue";

export default {
  components: {
    TheHeader,
    BaseCard,
    AddResource,
    StoredResource,
  },
  data() {
    return {
      activeComp: "stored-resource",
      storedData: [
        {
          title: "Google",
          description: "learn to google stuff",
          link: "https://www.w3schools.com",
          id: 1576996323453,
        },
      ],
    };
  },
  provide() {
    return {
      data: this.storedData,
      changeComponent: this.changeComponent,
    };
  },
  methods: {
    changeComponent(cmp) {
      this.activeComp = cmp;
    },
  },
  computed: {
    setAddResource() {
      return this.activeComp == "add-resource" ? "flat" : "text";
    },
    setStoredResource() {
      return this.activeComp == "stored-resource" ? "flat" : "text";
    },
  },
};
</script>
<style scoped></style>
