<template>
    <div class="search-wrapper" >
    <input
      @input="changeQuery"
      type="text"
      name="query"
      class="form-control form-control-lg search-input"
      autofocus>
    <i @click="onReset" class="bt-close fa fa-times-circle" />
  </div>
</template>

<script>
    import ButtonClose from './form/ButtonClose.vue';

    export default {
        name: 'SearchCp',
        components: { ButtonClose },
        data() {
            return {query: ''}
        },
        methods: {
            changeQuery(e) {
            this.query = e.target.value;
            this.$emit('@change', this.query);
            },
            onReset() { // 검색어 삭제
            const input = document.querySelector('.search-input');
            this.query = '';
            input.value = '';
            input.focus();
            this.$emit('@change', this.query);
            },
        },
    }
</script>

<style lang="scss" scoped="scoped">

.search-wrapper{
    @include rel;
    .bt-close{
      font-size: 1.25em;
      @include layer($t:calc(50% - .5em), $r:.5em);
    }
}

</style>