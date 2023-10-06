<template>
  <v-card class="cardColor" width="700" rounded="xl" elevation="6">
    <v-card-title class="text-center pt-6"> Add Form </v-card-title>

    <v-form ref="form" class="pa-4 pt-4">
      <v-row class="mx-5">
        <v-col>
          <v-text-field
            variant="outlined"
            v-model="FormName"
            label="Form name"
            hint="Enter the name of Form."
            required
          ></v-text-field>
        </v-col>
      </v-row>
      <v-card-actions>
        <v-btn variant="elevated" color="black">Back to list</v-btn>
        <v-spacer></v-spacer>
        <v-btn variant="elevated" color="black" @click="addQuestion"
          >Add questions</v-btn
        >
      </v-card-actions>
    </v-form>
  </v-card>
</template>

<script setup>
import { ref } from "vue";
import { useStore } from "../store/app";
const store = useStore();

const FormName = ref("");

function addQuestion() {
  store.currentFormNumber++;
}
</script>

<style scoped>
.cardColor {
  background-color: rgba(255, 250, 250, 0.4);
  color: #131111;
}
</style>
