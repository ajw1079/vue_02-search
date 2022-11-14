<template>
  <button @click="onClick">
      <i class="fa fa-times"></i>
  </button>
</template>

<script>
export default {
  name: 'ButtonClose',
  methods: {
    onClick() {
      this.$emit('@click');
    },
  },
};
</script>

<style lang="scss" scoped>
  button {
      border:none;
      background-color: transparent;
      cursor: pointer;
      font-size: 1.25em;
      @include layer($t:calc(50% - .5em), $r:.5em);
  }
</style>
