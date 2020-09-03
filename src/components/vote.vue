<template>
    <div class="buttons">
      <button v-for="(emoticon, index) in emoticons" 
              :key="index"
              :id="emoticon"
              :value="emoticon"
              class="btn-emoticons"
              @click="vote"
      ></button> <!-- For loop pada vue js-->
    </div>
  </template>
  
  <script>
  // @ is an alias to /src
  // import HelloWorld from "@/components/HelloWorld.vue";
  import moment from "moment";

  export default {
    name: "Home",
    components: { },
    data: function(){
        return {
            emoticons: ['very-bad', 'bad', 'ok', 'good', 'very-good']
        }
    },
    methods:{
        vote(e){
            var voted = e.target.value;

            var tgl = moment().format('YYYY-MM-DD h:mm:ss');

            var data = {
                vote: voted,
                create_at: tgl
            }

            console.log(data);

            var jsonToString = JSON.stringify(data);

            console.log(jsonToString);

            localStorage.setItem('vote', jsonToString);
        }
    }
  };
  </script>
  
  <style type="text/css">
    .buttons{
        display: flex;
    }

    .btn-emoticons{
        background: url("~@/assets/emoticon.png");
        width: 101px;
        height: 100px;
        border: none;
        margin: 0px 10px;
        outline: none;
        cursor: pointer;
    }

    #very-bad{
        background-position: 0px 0px;
    }
    #very-bad:hover{
        background-position: 0px -100px;
    }
    #very-bad:active{
        background-position: 0px -200px;
    }

    #bad{
        background-position: -101px 0px;
    }
    #bad:hover{
        background-position: -101px -100px;
    }
    #bad:active{
        background-position: -101px -200px;
    }

    #ok{
        background-position: -202px 0px;
    }
    #ok:hover{
        background-position: -202px -100px;
    }
    #ok:active{
        background-position: -202px -200px;
    }

    #good{
        background-position: -303px 0px;
    }
    #good:hover{
        background-position: -303px -100px;
    }
    #good:active{
        background-position: -303px -200px;
    }

    #good{
        background-position: -303px 0px;
    }
    #good:hover{
        background-position: -303px -100px;
    }
    #good:active{
        background-position: -303px -200px;
    }

    #very-good{
        background-position: -404px 0px;
    }
    #very-good:hover{
        background-position: -404px -100px;
    }
    #very-good:active{
        background-position: -404px -200px;
    }
  </style>