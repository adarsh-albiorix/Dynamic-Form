<template>
  <!-- <v-container> -->
  <v-card image="../assets/bg.jpg" flat height="700">
    <template class="d-flex justify-center">
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
    </template>
    <template class="d-flex justify-center mt-16">
      <div class="step-content card-color">
        <transition name="fade" mode="out-in">
          <component
            height=""
            :is="Forms[currentFormNumber]"
            :key="currentFormNumber"
          />
          <!-- @validation="handleEvents"
                  @Data="handleData" -->
        </transition>
      </div>
    </template>
  </v-card>
  <!-- </v-container> -->
</template>

<script setup>
import { ref, reactive, markRaw } from "vue";
import { useRouter } from "vue-router";
import FormName from "./FormName.vue";

const router = useRouter();
const currentFormNumber = ref(0);

const Forms = reactive([markRaw(FormName)]);

function navigateToEditPage() {
  router.push("/edit");
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
