<template>
  <div>
    <h2>ここは子コンポーネント</h2>
    <hr />
    <p>Title: {{ value.title }}</p>
    <p>count: {{ value.count }}</p>
    <v-btn class="info" @click="handleClick"></v-btn>
  </div>
</template>
<script>
import { defineComponent } from "@vue/composition-api";

export default defineComponent({
  props: {
    value: {
      type: Object,
      default: null,
    },
  },
  setup(_, context) {
    const handleClick = () => {
      console.log("handleClick");
      context.emit("my-event", 11, "hoge");
    };

    return { handleClick };
  },
});
</script>
