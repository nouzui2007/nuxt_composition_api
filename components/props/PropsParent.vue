<template>
  <v-card>
    <v-card-title> Composition APIで親子間データ受け渡し </v-card-title>
    <v-card-subtitle
      >Propsを利用した親から子へのデータ渡しサンプル</v-card-subtitle
    >
    <v-card-text>
      <PropsChild
        @my-event="handleEvent"
        :title="titleValue"
        :count="counter"
      />
    </v-card-text>
  </v-card>
</template>
<script>
import { defineComponent, ref } from "@vue/composition-api";
import PropsChild from "./PropsChild";

export default defineComponent({
  components: { PropsChild },
  setup() {
    const titleValue = ref("タイトル");
    const counter = ref(123);

    const handleEvent = (...args) => {
      console.log("子コンポーネントのイベント発生");
      console.log(args);
    };

    return {
      titleValue,
      counter,
      handleEvent,
    };
  },
});
</script>
