<!--CATATAN
:class="{active: emoticon == emoticonClick}" artinya jika nilai emoticon hasil looping tersebut memiliki nilai emoticon yang sedang di klik maka emoticon yg di klik tersebut memiliki class active
-->
<template>
    <div class="buttons">
      <button v-for="(emoticon, index) in emoticons" 
              :key="index"
              :id="emoticon"
              :value="emoticon"
              class="btn-emoticons"
              :class="{active: emoticon == emoticonClick}" 
              :disabled="isDisable"
              @click="vote"
      ></button> <!-- For loop pada vue js-->
    </div>
  </template>
  
  <script>
  // @ is an alias to /src
  // import HelloWorld from "@/components/HelloWorld.vue";
  import moment from "moment";

  export default {
    name: "vote",
    props: {
        voteProp: {
            type : Function
        }
    },
    data: function(){
        return {
            emoticons: ['very-bad', 'bad', 'ok', 'good', 'very-good'],
            emoticonClick : ''
        }
    },
    methods:{
        vote(e){
            var voted = e.target.value;
            //untuk menentukan button dengan class active
            this.emoticonClick = voted;

            //melakukan penyimpanan data
            this.store(voted);

            //memberikan indikator ke home components untuk menampilkan terima kasih
            this.voteProp();
        },
        store(voted){
            var keyStorage = moment().format('YYYYMMDDhhmmss');
            var tgl = moment().format('YYYY-MM-DD h:mm:ss');

            var data = {
                vote: voted,
                create_at: tgl
            }

            console.log(data);

            var jsonToString = JSON.stringify(data);

            console.log(jsonToString);

            localStorage.setItem(keyStorage, jsonToString);
        }
    },
    computed:{
        isDisable : function(){
            return this.emoticonClick.length === 0 ? false : true;
        }
    },
    mounted(){
        this.$root.$on('emitProcessDone', () => {
            this.emoticonClick = '';
        });
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
    #very-bad.active,
    #very-bad:active{
        background-position: 0px -200px;
    }

    #bad{
        background-position: -101px 0px;
    }
    #bad:hover{
        background-position: -101px -100px;
    }
    #bad.active,
    #bad:active{
        background-position: -101px -200px;
    }

    #ok{
        background-position: -202px 0px;
    }
    #ok:hover{
        background-position: -202px -100px;
    }
    #ok.active,
    #ok:active{
        background-position: -202px -200px;
    }

    #good{
        background-position: -303px 0px;
    }
    #good:hover{
        background-position: -303px -100px;
    }
    #good.active,
    #good:active{
        background-position: -303px -200px;
    }

    #very-good{
        background-position: -404px 0px;
    }
    #very-good:hover{
        background-position: -404px -100px;
    }
    #very-good.active,
    #very-good:active{
        background-position: -404px -200px;
    }
  </style>