<template>
  <v-card image="../assets/bg.jpg" flat height="1000">
    <transition name="fade" mode="out-in">
      <span v-if="show" class="d-flex justify-center">
        <div>
          <v-btn
            class="mt-16"
            icon="mdi-plus"
            color="blue-grey"
            @click="navigateToEditPage"
          >
          </v-btn>
        </div>
        <div>
          <v-card-title class="mt-16 label" style="font-size: xx-large"
            >Click the button to Add the form</v-card-title
          >
        </div>
      </span>
    </transition>

    <template class="d-flex justify-center mt-16">
      <div class="step-content card-color">
        <transition name="fade" mode="out-in">
          <component
            height=""
            :is="Forms[store.currentFormNumber]"
            :key="store.currentFormNumber"
          />
        </transition>
      </div>
    </template>
  </v-card>
</template>

<script setup>
import { reactive, markRaw, ref } from "vue";
import { useStore } from "../store/app";
import FormName from "./FormName.vue";
import AddQuestions from "./AddQuestions.vue";

const store = useStore();
const show = ref(true);

const Forms = reactive([markRaw(FormName), markRaw(AddQuestions)]);

function navigateToEditPage() {
  store.currentFormNumber = 0;
  show.value = false;
}
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inconsolata:wght@500&display=swap");
.label {
  font-family: "Inconsolata", monospace;
}
.card-color {
  border-color: white important;
  position: sticky;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
