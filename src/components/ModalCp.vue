<template>
  <div class="modal-wrapper" @click="onClose">
    <div class="modal-wrap">
      <img :src="list.src" :alt="list.title" class="w-100">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: ['list'],
  methods: {
    onClose() {
      this.$emit('@close');
    },
  },
};
</script>

<style lang="scss" scoped>
.modal-wrapper {
  @include layer($p: fixed, $l: 0, $t: 0, $i: 999);
  width: 100%;
  height: 100vh;
  background-color: rgba(0, 0, 0, .85);
  .modal-wrap {
    @include center;
    max-width: 60%;
    max-height: 80%;
  }
}
</style>