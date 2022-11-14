<template>
    <header class="heade-wrapper">
    <h1 class="logo-wrap">
      <img src="@/assets/img/cat-logo.png" alt="logo" class="logo">
      {{title}}
    </h1>
  </header>
</template>

<script>


export default {
    name: 'TitleCp',
    props: ['title'],
}
</script>

<style lang="scss" scoped>
.heade-wrapper{
  margin: auto;
  .logo-wrap{
      padding:$gutter-width;
      background-color: $secondary-color;
      color: $dark-color;
      font-size: 1em;
      display: flex;
      align-items: center;    
      margin-bottom: 1em;
      .logo{
          display: block;
          width: 2em;
          padding-right: .5em;
      }
  }
}
</style>