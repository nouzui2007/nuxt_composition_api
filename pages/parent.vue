<template>
  <div>
    <h1>{{ form.name }}</h1>
    <form @submit.prevent>
      <InputName v-model="form.name" />
    </form>
  </div>
</template>
<script>
import { defineComponent, reactive } from "@vue/composition-api";

export default defineComponent({
  setup() {
    const form = reactive({
      name: "山田",
    });

    return {
      form,
    };
  },
});
</script>
