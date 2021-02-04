<template>
  <ion-header>
    <ion-toolbar>
      <ion-title slot="start">Modal</ion-title>

      <ion-buttons slot="end">
        <ion-button @click="close()">
          <ion-icon name="close" size="large" slot="icon-only"></ion-icon>
        </ion-button>
      </ion-buttons>
    </ion-toolbar>
  </ion-header>

  <ion-content>
    <ion-list>
      <ion-item @click="goBack()">
        <ion-label>Click here!</ion-label>
      </ion-item>
    </ion-list>
  </ion-content>
</template>

<script lang="ts">
import {
  IonButton,
  IonButtons,
  IonContent,
  IonHeader,
  IonIcon,
  IonItem,
  IonLabel,
  IonList,
  IonTitle,
  IonToolbar,
} from "@ionic/vue";
import { defineComponent } from "vue";
import { useRouter } from "vue-router";

export default defineComponent({
  components: {
    IonButton,
    IonButtons,
    IonContent,
    IonHeader,
    IonIcon,
    IonItem,
    IonLabel,
    IonList,
    IonTitle,
    IonToolbar,
  },

  props: {
    close: {
      type: Function,
      default: () => {
        return {};
      },
    },
  },

  setup() {
    const router = useRouter();
    const goBack = () => router.back();

    return {
      goBack,
    };
  },
});
</script>
