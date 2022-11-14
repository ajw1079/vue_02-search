<template>
    <div id="app" class="container mb-4">
        <Title :title="mainTitle" />
        <Search @@change="onChangeQuery"/>
        <ListWrap @@click="onChangeList" :lists="searchCats" />
        <Modal v-show="isSelected" :list="cat" @@close="onCloseModal" />
    </div>
</template>

<script>
    import axios from 'axios';
    import Title from './components/TitleCp.vue';
    import Search from './components/SearchCp.vue';
    import ListWrap from './components/ListWrapCp.vue';
    import Modal from './components/ModalCp.vue';

    export default {
        name: 'App',
        components: {
            Title,
            Search,
            ListWrap,
            Modal
        },
        data() {
            return {
                mainTitle: 'Cat House',
                cats: [],
                cat: {},
                searchCats: [],
                isSelected: false
            }
        },
        async created() {
            const { data } = await axios.get('/json/cat.json');
            this.cats = data;
            this.searchCats = data;
        },
        methods: {
            onChangeQuery(query) {
            this.searchCats = this.cats.filter((v) => {
                const result = v.title.toLowerCase().includes(query.toLowerCase())
                                || v.description.toLowerCase().includes(query.toLowerCase())
                                || v.age.toLowerCase().includes(query.toLowerCase());
                return result;
            });
            },
            onChangeList(v) {
                this.cat = v;
                this.isSelected = true;
            },
            onCloseModal() {
                this.isSelected = false;
            },
        },
    }
</script>

<style lang="scss" scoped="scoped">
    @import '@/assets/scss/common';
    #app {
        margin-left: auto;
        margin-right: auto;
    }
    ul, ol{
        list-style: none;
        padding-left: 0;
    }


</style>