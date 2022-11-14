<template>
  <li class="list">
    <img
      @click="onClick"
      :src="list.src"
      :alt="list.title"
      class="w-100">
    <h2>{{ list.title }}</h2>
  </li>
</template>

<script>
export default {
  name: 'List',
  props: ['list'],
  methods: {
    onClick(e) {
      this.$emit('@click', { src: e.target.src, title: e.target.alt });
    },
  },
};
</script>

<style lang="scss" scoped>
.list {
  border-radius: 5px;
  overflow: hidden;
  height: 200px;
  @include rel;
  width: 23%;
  margin-right: 2%;
  margin-bottom: 2%;
  border: 1px solid $primary-color;
  cursor: pointer;
  @include LG {
    width: 31.3333%;
  }
  @include MD {
    width: 48%;
  }
  @include SM {
    width: 98%;
  }

  img{
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  h2 {
    @include layer($l: 0, $b: 0);
    width: 100%;
    padding: 1em;
    text-align: center;
    background-color: rgba(0, 0, 0, .5);
    color: $light-color;
    font-size: 1.25em;
  }
}
</style>