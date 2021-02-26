<template>
  <ion-page>
    <ion-header translucent>
      <ion-toolbar>
        <ion-title>Page 1</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content fullscreen>
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Page 1</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-refresher slot="fixed" @ionRefresh="doRefresh($event)">
        <ion-refresher-content></ion-refresher-content>
      </ion-refresher>

      <ion-list>
        <ion-item>
          <ion-label class="ion-text-wrap" button @click="goForward()">
            Go to Page 2
          </ion-label>
        </ion-item>
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import {
  IonContent,
  IonHeader,
  IonItem,
  IonLabel,
  IonPage,
  IonTitle,
  IonToolbar,
  IonList,
  IonRefresher,
  IonRefresherContent,
} from "@ionic/vue";
import { defineComponent, ref, watch } from "vue";
import { useRouter } from "vue-router";

export default defineComponent({
  name: "page1",

  components: {
    IonContent,
    IonHeader,
    IonItem,
    IonLabel,
    IonPage,
    IonToolbar,
    IonTitle,
    IonList,
    IonRefresher,
    IonRefresherContent,
  },

  setup() {
    const router = useRouter();
    const radio = ref("red");
    const goForward = () => router.push({ name: "page2" });

    const doRefresh = (event: any) => {
      console.log("Begin async operation");

      setTimeout(() => {
        console.log("Async operation has ended");
        event.target.complete();
      }, 2000);
    };

    return {
      radio,
      goForward,
      doRefresh,
    };
  },
});
</script>

<style>
</style>