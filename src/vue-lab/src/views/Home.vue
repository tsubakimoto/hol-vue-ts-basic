<template>
  <div class="home">
    <h3>テキストバインディング</h3>
    <span>{{ msg }}</span>

    <h3>リストレンダリング</h3>
    <ul id="item-list">
      <li v-for="item in items" :key="item.id">{{ item.name }}</li>
    </ul>

    <h3>イベントハンドリング</h3>
    <button v-on:click="onClick">実行</button>

    <h3>算出プロパティ</h3>
    <p>{{ computedMsg }}</p>

    <h3>条件付きレンダリング</h3>
    <button v-on:click="showDetail">表示</button>
    <div v-if="detail">詳細が表示されました。</div>

    <h3>エラー</h3>
    <button v-on:click="raiseError">エラー</button>
    <div v-bind:class="{ 'text-danger': hasError}">システムからのメッセージ</div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

declare interface Item {
  id: number;
  name: string;
}

export default Vue.extend({
  data() {
    return {
      msg: "Hello Vue.js!",
      items: [
        {
          id: 1,
          name: "キーボード"
        },
        {
          id: 2,
          name: "マウス"
        }
      ] as Item[],
      detail: false,
      hasError: false
    };
  },
  methods: {
    onClick(): void {
      alert(this.msg);
    },
    showDetail(): void {
      this.detail = true;
    },
    raiseError(): void {      
      this.hasError = true;
    }
  },
  computed: {
    computedMsg(): string {
      return this.msg.replace(/!/g, "") + " + TypeScript!";
    }
  }
});
</script>

<style scoped>
.home {
  text-align: left;
}
.text-danger {
  color: darkred;
}
</style>