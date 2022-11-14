<template>
  <ul class="mt-4">
    <List
      v-for="v in lists"
      :key="v.id"
      :list="v"
      @@click="onClick" />
  </ul>
</template>

<script>
import List from './ListCp.vue';
export default {
  name: 'ListWrap',
  components: { List },
  props: ['lists'],
  methods: {
    onClick(v) {
      this.$emit('@click', v);
    },
  },
};
</script>

<style lang="scss" scoped>
ul {
  width: 102%;
  @include flex($w: wrap, $v: flex-start);
}
</style>