<script setup>
defineProps({
  btnText: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    default:
      'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
  },
})
</script>

<template>
  <v-dialog max-width="500">
    <template v-slot:activator="{ props: activatorProps }">
      <v-btn v-bind="activatorProps" color="surface-variant" :text="btnText" variant="flat"></v-btn>
    </template>

    <template v-slot:default="{ isActive }">
      <v-card :title="btnText">
        <v-card-text>
          {{ description }}
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn text="關閉" @click="isActive.value = false"></v-btn>
        </v-card-actions>
      </v-card>
    </template>
  </v-dialog>
</template>
