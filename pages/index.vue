<template lang="pug">
.home
  h1.home__title
    |麻雀点数計算
  .home__body
    .home__item
      |符：
      input(
        v-model="fu"
        type="number"
        )
    .home__item
      |上がりの翻数（ドラを含む）：
      input(
        v-model="fan"
        type="number"
        )
    .home__total
      h2.home__total-title 点数
      .home__total-row
        |自家子ツモ：子{{ ko }} / 親{{ oya }}
</template>

<script>
export default {
  data() {
    return {
      fu: 0,
      fan: 0,
    };
  },
  computed: {
    base() {
      const fu = Math.ceil(this.fu / 10) * 10;
      return fu * Math.pow(2, this.fan) * 2 * 2;
    },
    oya() {
      return Math.ceil((this.base * 2) / 100) * 100;
    },
    ko() {
      return Math.ceil(this.base / 100) * 100;
    },
  },
};
</script>

<style lang="scss">
.home {
  &__title {
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system,
      BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial,
      sans-serif;
    display: block;
    color: #35495e;
    letter-spacing: 1px;
  }
}
</style>
