<template>
  <div class="troll">
    <img :src="randomTroll().imageUrl" alt="Avatar" style="width:100%">
    <div class="container">
      <h4><b>{{imageTitle}}</b></h4>
      <p><span>Ref Link : </span><a :href="imageLink" target="_blank">{{imageLink}}</a></p>
      <button class="button dec" @click="randomTroll()">Find Daily Mode</button>
    </div>
  </div>
</template>

<script>
    export default {
        name: "trollview",
        props: ['links'],
        data() {
            return {
                link: 0,
                imageLink: '',
                imageUrl: '',
                imageTitle: ''
            }
        },
        methods: {

            randomTroll() {

                console.log(this.links.length);

                let link = this.links[(Math.floor(Math.random() * this.links.length))];

                this.imageUrl = link.images.fixed_height.url;
                this.imageTitle = link.title;
                this.imageLink = link.bitly_gif_url;

                return {imageTitle: this.imageTitle, imageUrl: this.imageUrl, imageLink: this.imageLink}
            }
        }
    }
</script>
<style scoped>

  .troll {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    width: 40%;
    display: inline-block;
    background-color: whitesmoke;
    text-align: center;
    position: absolute;
    left: 30%;
    margin-top: 70px;
  }

  .troll:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
  }

  .container {
    padding: 2px 16px;
  }

  .button {

    /*border-radius: 5px;
    background-color: #FD644E;
    width: 100px;
    height: 30px;
    margin: 10px;
    color: white;*/

    display: inline-block;
    margin: 0.75rem;
    padding: 0.75rem 1.5rem;
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

  .dec:hover {
    /*background-color: tomato;
    color: white;*/
    border-color: tomato;
    background-color: whitesmoke;
    color: black;
  }
</style>
