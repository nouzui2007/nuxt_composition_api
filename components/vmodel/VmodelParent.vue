<template>
  <v-card>
    <v-card-title> Composition APIで親子間データ受け渡し </v-card-title>
    <v-card-subtitle
      >Propsを利用した親から子へのデータ渡しサンプル</v-card-subtitle
    >
    <v-card-text>
      <VmodelChild @my-event="handleEvent" v-model="target" />
    </v-card-text>
  </v-card>
</template>
<script>
import { defineComponent, reactive, ref } from "@vue/composition-api";
import VmodelChild from "./VmodelChild";

export default defineComponent({
  components: { VmodelChild },
  setup() {
    const target = reactive({
      title: "タイトル",
      count: 123,
    });

    const handleEvent = (...args) => {
      console.log("子コンポーネントのイベント発生");
      console.log(args);
    };

    return {
      target,
      handleEvent,
    };
  },
});
</script>
