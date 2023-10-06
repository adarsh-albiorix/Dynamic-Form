<template>
  <v-card class="cardColor" width="700" rounded="xl" elevation="6">
    <v-card-title class="text-center pt-6"> Add Questions </v-card-title>

    <v-form ref="form" class="pa-4 pt-4">
      <v-row class="mx-5">
        <v-col cols="12" md="4">
          <v-text-field
            variant="outlined"
            label="Question"
            v-modal="Question"
            required
          ></v-text-field>
        </v-col>
        <v-col cols="12" md="4">
          <v-select
            v-model="selectedType"
            variant="outlined"
            :items="types"
            label="Type"
            required
          ></v-select>
        </v-col>
        <v-col cols="12" md="4">
          <v-select
            v-model="selectedValidations"
            :items="Validations"
            variant="outlined"
            chips
            label="Validations"
            multiple
            required
          ></v-select>
        </v-col>
      </v-row>
      <v-row class="mx-5">
        <v-col cols="12" md="6">
          <v-text-field
            variant="outlined"
            v-model="minNumber"
            label="Enter min number"
            type="number"
          ></v-text-field>
        </v-col>
        <v-col cols="12" md="6">
          <v-text-field
            variant="outlined"
            v-model="maxNumber"
            label="Enter max number"
            type="number"
          ></v-text-field>
        </v-col>
      </v-row>
      <v-row justify="center">
        <v-btn variant="outlined" color="black"> Add more questions </v-btn>
      </v-row>
      <v-card-actions>
        <v-btn variant="elevated" color="black" @click="back">Back</v-btn>
        <v-spacer></v-spacer>
        <v-btn variant="elevated" color="black" @click="submit">Submit</v-btn>
      </v-card-actions>
    </v-form>
  </v-card>
</template>

<script setup>
import { ref } from "vue";
import { useStore } from "../store/app";
const store = useStore();

const Question = ref("");
const selectedType = ref(null);
const selectedValidations = ref([]);
const minNumber = ref(null);
const maxNumber = ref(null);

const Validations = ["required", "minLength", "maxLength"];

const types = ["Text", "Number", "TextArea", "Date", "Dropdown", "radio"];
function submit() {
  store.currentFormNumber++;
}
function back() {
  store.currentFormNumber--;
}
</script>

<style scoped>
.cardColor {
  background-color: rgba(255, 250, 250, 0.4);
  color: #131111;
}
</style>
