<template>
  <ion-page class="ion-page">
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button default-href="/" />
        </ion-buttons>

        <ion-title>Child Page</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content>
      <ion-item>
        <ion-label class="ion-text-wrap"> Label </ion-label>
      </ion-item>

      <ion-button @click="goBack()">GO BACK</ion-button>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { useRouter } from "vue-router";
import {
  IonBackButton,
  IonButton,
  IonButtons,
  IonContent,
  IonHeader,
  IonItem,
  IonLabel,
  IonPage,
  IonToolbar,
  IonTitle,
} from "@ionic/vue";

export default defineComponent({
  name: "childPage",
  components: {
    IonBackButton,
    IonButton,
    IonButtons,
    IonContent,
    IonHeader,
    IonItem,
    IonLabel,
    IonPage,
    IonToolbar,
    IonTitle,
  },

  setup() {
    const router = useRouter();
    const goBack = () => {
      console.log("GO BACK");
      router.go(-2);
    };

    return {
      goBack,
    };
  },
});
</script>

<style>
</style>