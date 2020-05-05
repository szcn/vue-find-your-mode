<template>
  <div id="app">
    <img v-if="isLoading" src="./assets/5.gif">
    <trollview :links="links"></trollview>
    <search v-on:searchReq="handleSearch"></search>
  </div>
</template>

<script>
    import trollview from "./components/trollview";
    import search from "./components/search";

    export default {
        name: 'app',
        components: {trollview, search},
        data() {
            return {
                isLoading: true,
                links: []
            }
        },
        methods: {

            doQuery(apiUrl){
                fetch(apiUrl)
                    .then(res => res.json())
                    .then(links => {
                        this.links = links.data;
                        this.isLoading=false;
                    })

            },
            handleSearch(query) {
                this.links =[];
                this.isLoading =true;
                const apiUrl = `http://api.giphy.com/v1/gifs/search?q=${query}&limit=1000&api_key=wGwPtA37qjwXXUMvbkhinLZ07re8Umro`;
                this.doQuery(apiUrl);

            }

        },
        created() {
            const apiUrl = 'http://api.giphy.com/v1/gifs/search?q=work&limit=1000&api_key=wGwPtA37qjwXXUMvbkhinLZ07re8Umro';
            this.doQuery(apiUrl);
        }
    }
</script>

<style lang="scss">

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
</style>
