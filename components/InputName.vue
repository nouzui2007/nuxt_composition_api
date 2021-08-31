<template>
  <div>
    <label for="name">お名前</label>
    <input
      type="text"
      id="name"
      :value="value"
      @input="$emit('input', $event.target.value)"
    />
    <v-text-field
      prepend-icon="mdi-account-circle"
      label="ユーザ名"
      :value="value"
    />
  </div>
</template>
<script>
import { defineComponent } from "@vue/composition-api";

export default defineComponent({
  //   setup() {},
  props: {
    value: {
      type: String,
      requred: true,
    },
  },
});
</script>
