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

      <ion-list>
        <ion-radio-group v-model="radio">
          <ion-item>
            <ion-label>Red</ion-label>
            <ion-radio value="red"></ion-radio>
          </ion-item>
          <ion-item>
            <ion-label>Green</ion-label>
            <ion-radio value="green"></ion-radio>
          </ion-item>
          <ion-item>
            <ion-label>Blue</ion-label>
            <ion-radio value="blue"></ion-radio>
          </ion-item>
        </ion-radio-group>

        <ion-item>
          <ion-label slot="start">Color selected</ion-label>
          <ion-label slot="end">{{ radio }}</ion-label>
        </ion-item>
      </ion-list>

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
  IonRadio,
  IonRadioGroup,
  IonList,
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
    IonRadio,
    IonRadioGroup,
    IonList,
  },

  setup() {
    const router = useRouter();
    const radio = ref("red");
    const goForward = () => router.push({ name: "page2" });

    watch(
      () => radio.value,
      (newValue) => console.log(newValue)
    );

    return {
      radio,
      goForward,
    };
  },
});
</script>

<style>
</style>