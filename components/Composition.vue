<template>
  <div>
    <h1>{{ title }}</h1>
    <h2>ユーザ追加</h2>
    <form @submit.prevent>
      <div>
        <label for="name">お名前</label>
        <input id="name" type="text" v-model="data.form.name" />
      </div>
      <div>
        <button @click="addUser">ユーザー追加</button>
      </div>
    </form>
    <h2>ユーザー件数：{{ userNum }}</h2>
    <ul>
      <li v-for="u in data.users" :key="u.id">{{ u.id }} {{ u.name }}</li>
    </ul>
  </div>
</template>
<script>
import {
  defineComponent,
  reactive,
  ref,
  computed,
  watch,
} from "@vue/composition-api";

export default defineComponent({
  setup() {
    const data = reactive({
      form: {
        name: "",
      },
      users: [
        { id: 1, name: "加藤かな" },
        { id: 2, name: "田中紘一" },
        { id: 3, name: "山田太郎" },
      ],
    });
    const title = ref("タイトル");

    // createdは普通の処理。DOMにはさわれないが、setup内の変数にはアクセスできる
    // APIからデータを取ったりすることに利用
    setTimeout(() => {
      data.users.push({ id: 4, name: "新藤誠" });
      title.value = "タイトルが変更できること";
    }, 3000);

    // computedはこんな感じで定義
    const userNum = computed(() => data.users.length);

    // methodsに定義していた関数は、通常の関数として定義できる
    const addUser = () => {
      const id = Math.max(...data.users.map((u) => u.id)) + 1;
      data.users.push({ id: id, name: data.form.name });
      data.form.name = "";
      refA.value = "hogehoge";
      refC.value = "hoge";
    };

    // watch は第一引数の値を監視して何らかの処理を実行する
    // 監視対象が１つ
    const refA = ref("REF A");
    watch(refA, () => {
      console.log("監視対象１つの何かの処理");
    });

    // 監視対象が複数の時はタプルを使う
    const refB = ref("REF B");
    const refC = ref("REF C");
    watch([refB, refC], () => {
      console.log("監視対象２つの時の何かの処理");
    });

    // リアクティブな値を全部
    // watch(() => {
    //   console.log("リアクティブな値を全部監視しての何かの処理");
    // });

    // 監視対象をリアクティブな値の一部にする
    watch(
      () => data.form.name,
      (currentName, prevName) => {
        console.log("Current Name:", currentName, " Previous Name: ", prevName);
      }
    );

    return {
      data,
      title,
      userNum,
      addUser,
    };
  },
});
</script>
