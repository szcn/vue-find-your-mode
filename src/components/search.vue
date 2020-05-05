<template>
  <div class="search">

    <input type="text" class="searchModeInput" v-model="query" @keypress.enter="handleSearch"/>
    <button class="searchModeBtn dec" @click="handleSearch">Search Daily Mode</button>


  </div>

</template>

<script>
    export default {
        name: "search",
        data() {

            return {
                query: ''
            }
        },
        methods: {

            handleSearch() {

                this.$emit('searchReq', this.query);

            }

        }
    }
</script>

<style scoped>

  .search {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    width: 40%;
    height: 8%;
    display: inline-block;
    background-color: whitesmoke;
    text-align: center;
    position: absolute;
    left: 30%;
  }

  .searchModeBtn {

    /*border-radius: 5px;
    background-color: #FD644E;
    width: 100px;
    height: 30px;
    margin: 10px;
    color: white;*/

    display: inline-block;
    margin: 0.55rem;
    padding: 0.45rem 0.5rem;
    border-radius: 0.1875rem;
    outline: none;
    /*background-color: white;
    color: black;*/
    font-family: inherit;
    font-size: 1.25em;
    font-weight: 400;
    line-height: 1.5rem;
    text-decoration: none;
    text-align: center;
    cursor: pointer;
    transition: all 150ms ease-out;
    /*border-color: tomato;*/
    background-color: tomato;
    color: white;
  }

  .searchModeInput {

    display: inline-block;
    margin: 0.55rem;
    padding: 0.45rem 0.5rem;
    border-radius: 0.1875rem;
    outline: none;
    /*background-color: white;
    color: black;*/
    font-family: inherit;
    font-size: 1.25em;
    font-weight: 400;
    line-height: 1.5rem;
    text-decoration: none;
    cursor: pointer;
    transition: all 150ms ease-out;
    width: 60%;
  }

  .dec:hover {
    /*background-color: tomato;
    color: white;*/
    border-color: tomato;
    background-color: whitesmoke;
    color: black;
  }

</style>
