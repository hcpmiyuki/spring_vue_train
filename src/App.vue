<template>
  <div id="app">
    <link href="https://fonts.googleapis.com/earlyaccess/nicomoji.css" rel="stylesheet">
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.7.2/css/all.css" integrity="sha384-fnmOCqbTlWIlj8LyTjo7mOUStjsKC4pOpQbqyi7RrhN7udi9RwhKkMHpvLbHG9Sr" crossorigin="anonymous">

    <div :class = "{wrapper:searched_member != null}">
    <header id = "top">
      <p class = "wf-nicomoji">#のぎまに</p>
      <a>毎週月曜日8時更新！乃木坂46の握手会神対応ランキング！</a>
      <p id = "search">推しの順位は？
        <input type = "text"　size = "15" placeholder = "例:白石麻衣" v-model = "search_name">
        <a id = "search_btn" class = "point" @click="Search()">検索</a>
        <p :class = "{validation:validation1}">名前が入力されていません</p>
        <p :class = "{validation:validation2}">名前が正しく入力されていません</p>
      </p>
    </header>

    <div class = "rank">
      <p class = "wf-nicomoji">ランキング</p>
      <div v-for = "member in results">
        <div :class = "{ppl:member.rank%2 == 0}">
            <!-- 1-3位 -->
            <div class="prof"  v-if = "member.rank <= 3">
              <a class = "rank-top point" @click="showMember(member.name)"><i class="fas fa-crown"></i>{{ member.rank }}位  {{ member.name }}</a><br>
              <img :src = "require('./assets/images/' + member.name + '.jpg')" :alt = "member.name">
            </div>
            <!-- 4-10位 -->
            <div class = "prof" v-if="member.rank >= 4 && member.rank <= 10">
              <a class = "point" @click="showMember(member.name)">{{ member.rank }}位  {{ member.name }}</a><br>
            </div>
            <!-- 以下 -->
            <div class = "prof" v-if="member.rank >= 11 && member.rank <= 36" :class="{hide_rank:hide}">
              <a class = "point" @click="showMember(member.name)">{{ member.rank }}位  {{ member.name }}</a><br>
            </div>
          </div>
      </div>

      <a @click = "hideRank()" :class="{hide_rank:!hide}" class = "point btn">もっとみる▼</a>
      <a @click = "showRank()" :class="{hide_rank:hide}" class = "point btn">とじる▲</a>
    </div>



    <footer>
      <a href = "#top">ページトップへ</a><br>
      <a><small>copyright</small> みゆき</a>
    </footer>
  </div>

    <div class = "modal" v-if = "searched_member != null">
      <p>{{searched_member[0].rank}}位
        <span v-if = "searched_member[0].rank > searched_member[3].rank"><i class="fas fa-level-down-alt"></i></span>
        <span v-if = "searched_member[0].rank < searched_member[3].rank"><i class="fas fa-level-up-alt"></i></span>
        <span v-if = "searched_member[0].rank == searched_member[3].rank">＝</span>
        {{searched_member[0].name}}
      </p>
      <div class="modal-contents">
        <img :src = "require('./assets/images/' + searched_member[0].name + '.jpg')" :alt = "searched_member[0].name"><br>
        <a>先週の順位：{{ searched_member[3].rank }}位</a><br>
        <a id = "line">
          <i class="fas fa-crown"></i>
          今週の神対応
          <i class="fas fa-crown"></i>
        </a><br>
        <a>
          {{ searched_member[0].tweet }}
        </a><br>
        <a class = "point" id = "close" @click="hideModal()">とじる×</a>
      </div>
    </div>

  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  data () {
    return {
      results: null,
      hide: true,
      search_name: null,
      searched_member: null,
      validation1: true,
      validation2: true
    }
  },
  methods:{
    hideRank: function(){
      if(this.hide){
        this.hide = false
      }else{
        thid.hide = true
      }
    },
    showRank: function(){
      if(!this.hide){
        this.hide = true
      }else{
        this.hide = false
      }
    },
    Search: function(){
      if(this.search_name){
        axios.get('http://localhost:5000/show/'+ this.search_name )
        .then((res) => {
          console.log(res.data)
          this.searched_member = res.data
          if(!this.searched_member){
            this.validation2 = false
          }else{
            this.validation1 = true
            this.validation2 = true
          }
        })
        .catch()
      }else{
        this.validation1 = false
      }
    },
    showMember: function(name){
      if(name){
        axios.get('http://localhost:5000/show/'+ name )
        .then((res) => {
          console.log(res.data)
          this.searched_member = res.data
        })
        .catch()
      }
    },
    hideModal: function(){
      this.searched_member = null
      this.search_name = null
    }

  },
  mounted(){
    axios.get('http://localhost:5000/results')
    .then((res) => {
      console.log(res.data)
      this.results = res.data
      console.log(this.results[2])
    })
    .catch()
  }
}
</script>

<style lang="scss">
$main-color: #b43ae2;
$sub-color: rgb(255, 255, 255);
$point-color: rgba(246, 203, 255,1);
/* スマホ */
@media screen and (min-width:0px){
  /*  全体　*/
  #app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    width: auto;
  }

  .validation{
    display: none;
  }

  .fa-crown{
    color: $main-color;
  }

  .wrapper{
    filter: grayscale(100%);
  }

  .point{
    cursor: pointer;
  }

  *{
    margin: 0px;
    padding: 0px;
  }

  a{
    display: inline-block;
  }

  /* ヘッダー */
  header{
    .wf-nicomoji{
      font-family: "Nico Moji";
      font-size: 75px;
      color: $main-color;
    }

    p{
      margin: 0px;
    }

    #search{
      background: $main-color;
    }

    #search_btn{
      background-color: $sub-color;
      font-size: 90%;
      margin: 6px;
      padding: 3px 6px;
      border-radius: 10px;
    }
  }

  /* ランキングのとこ */
  .rank{
    width: 90%;
    margin: 30px auto;
    border-radius: 10px;
    border: 1px $main-color;

    .rank-top{
      position: relative;
      padding: 0 20px;
      margin: 10px;

      &:after{
        content: "";
        display: block;
        height: 2px;
        background: -webkit-linear-gradient(to right, $point-color, $main-color);
        background: linear-gradient(to right, $point-color, $main-color);
      }
    }

    a{
      position: relative;
      padding: 0 20px;
      margin: 10px;
    }

    .wf-nicomoji{
      font-family: "Nico Moji";
      font-size: 33px;
      background-color: $main-color;
      border-top-left-radius: 9px;
      border-top-right-radius: 9px;
      color: $sub-color;
      margin: 0;
      padding: 5px;
    }

    img{
      width: 40%;
      height: auto;
      margin-bottom: 10px;
    }

    .btn{
      text-decoration: none;
      margin-top: 20px;
      color: $sub-color;
      font-weight: bold;
      background-color: $main-color;
      border-radius: 30px;
      padding: 6px;
    }

    // 文字のシマシマ
    .ppl{
      background-color: rgba(215, 47, 252, 0.1);
    }

    .hide_rank{
      display: none;
    }

  }


  /* フッター */
  footer{
    height: 50px;
    background-color: $main-color;
    bottom: 0;
  }

  // モーダru
  .modal{
    position: fixed;

    background-color: $sub-color;
    width: 80%;
    margin: 0px auto;
    border: 1px solid $main-color;
    border-radius: 10px;
    z-index: 100;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);

    .modal-contents{
      margin: 10px;
    }

    p{
      font-size: 120%;
      border-top-left-radius: 9px;
      border-top-right-radius: 9px;
      background-color: $main-color;
      padding: 5px;
      font-weight: bold;
      color: $sub-color;
    }


    img{
      width: 60%;
      height: auto;
      margin-bottom: 10px;
    }

    #line{
      position: relative;
      padding: 0 20px;
      margin: 10px;

      &:after{
        content: "";
        display: block;
        height: 2px;
        background: -webkit-linear-gradient(to right, $point-color, $main-color);
        background: linear-gradient(to right, $point-color, $main-color);
      }
    }

    .fa-handshake{
      color: $main-color;
    }
  }

  #close{
    color: $main-color;
    font-weight: bold;
  }


}

/* PC */
@media screen and (min-width:481px){
  header{
    p{
      font-size: 150%;
    }

    input{
      font-size: 100%;
    }
  }
  .rank{
    margin: 30px auto;
    border-radius: 10px;
    border: 1px solid $main-color;
    width: 50%;

    a{
      position: relative;
      padding: 0 20px;
      margin: 10px;
      font-size: 20px;
    }

    img{
      width: 20%;
      height: auto;
      margin-bottom: 10px;
    }
  }

  // モーダru
  .modal{
    position: fixed;
    background-color: $sub-color;
    width: 60%;
    margin: 0px auto;
    border-radius: 10px;
    z-index: 100;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);



    img{
      width: 30%;
      height: auto;
      margin-bottom: 10px;
    }
  }

}

</style>
