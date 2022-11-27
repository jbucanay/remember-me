<template>
  <v-snackbar v-model="snackbar">
    <slot name="success"></slot>
    <template v-slot:actions>
      <v-btn color="pink" variant="text" @click="showToast"> Close </v-btn>
    </template>
  </v-snackbar>
</template>

<script>
export default {
  props: ["snacks"],
  data() {
    return {
      snackbar: this.snacks,
    };
  },
  methods: {
    showToast() {
      console.log(this.showSnack);
    },
  },
};
</script>
