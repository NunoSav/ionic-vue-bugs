<template>
  <ion-page class="ion-page">
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button default-href="/" />
        </ion-buttons>

        <ion-title>Page 2</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content>
      <ion-item>
        <ion-label class="ion-text-wrap" button @click="go()">
          GO TO ChildPage
        </ion-label>
      </ion-item>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import {
  IonBackButton,
  IonButtons,
  IonContent,
  IonHeader,
  IonItem,
  IonLabel,
  IonPage,
  IonToolbar,
  IonTitle,
} from "@ionic/vue";
import { useRouter } from "vue-router";

export default defineComponent({
  name: "page2",
  components: {
    IonBackButton,
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
    const go = () => {
      console.log("GO");
      router.push({
        name: "childPage",
      });
    };

    return {
      go,
    };
  },
});
</script>

<style>
</style>