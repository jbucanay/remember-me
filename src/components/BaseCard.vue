<template>
  <v-card
    variant="elevated"
    elevation="5"
    width="700"
    class="mt-10"
    rounded="30"
  >
    <slot name="buttons"></slot>
    <slot name="storedResource"></slot>
    <slot name="addResource"></slot>
  </v-card>
</template>

<script>
export default {};
</script>
