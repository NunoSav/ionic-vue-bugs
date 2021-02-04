<template>
  <ion-page>
    <ion-header translucent>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button />
        </ion-buttons>

        <ion-title>Page 2</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content fullscreen>
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Page 2</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-item>
        <ion-label class="ion-text-wrap" button @click="showModal()">
          Show Modal
        </ion-label>
      </ion-item>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineAsyncComponent, defineComponent } from "vue";
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
  modalController,
} from "@ionic/vue";

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
    const showModal = async (): Promise<void> => {
      try {
        const modal = await modalController.create({
          component: defineAsyncComponent(
            () => import("@/components/Modal.vue")
          ),
          componentProps: {
            close: () => {
              modal.dismiss();
            },
          },
          swipeToClose: true,
        });

        await modal.present();
      } catch (error) {
        console.error(error.message);
      }
    };

    return {
      showModal,
    };
  },
});
</script>

<style>
</style>