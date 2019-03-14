<template>
  <div id="app">
    <link href="https://fonts.googleapis.com/earlyaccess/nicomoji.css" rel="stylesheet">
    <header id = "top">
      <p class = "wf-nicomoji">#のぎまに</p>
      <a>毎週月曜日hoge時更新！乃木坂46の握手会神対応ランキング！(流れる)</a>
      <p id = "search">推しの順位は？
        <input type = "text"　size = "15" placeholder = "例:白石麻衣">
        <input type = "submit" value = "検索">
      </p>
    </header>

    <div class = "rank">
      <p class = "wf-nicomoji">こんしゅうのランキング</p>
      <div v-for = "member in results">
        <div :class = "{ppl:member.rank%2 == 0}">
            <!-- 1-3位 -->
            <div class="prof"  v-if = "member.rank <= 3">
              <a class = "rank-top">{{ member.rank }}位  {{ member.name }}</a><br>
              <img :src = "require('./assets/images/' + member.name + '.jpg')" :alt = "member.name">
            </div>
            <!-- 4-10位 -->
            <div class = "prof" v-if="member.rank >= 4 && member.rank <= 10">
              <a>{{ member.rank }}位  {{ member.name }}</a><br>
            </div>

            <div class = "prof" v-else :class="{hide_rank:hide}">
              <a>{{ member.rank }}位  {{ member.name }}</a><br>
            </div>
          </div>
      </div>

      <a @click = "hideRank()" :class="{hide_rank:!hide}">もっとみる▼</a>
      <a @click = "showRank()" :class="{hide_rank:hide}">とじる▲</a>
    </div>

    <footer>
      <a href = "#top">ページトップへ</a><br>
      <a><small>copyright</small> みゆき</a>
    </footer>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  data () {
    return {
      results: null,
      hide: true
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
/* スマホ */
@media screen and (min-width:0px){
  /*  全体　*/
  #app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    width: auto;
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
  }

  /* ランキングのとこ */
  .rank{
    width: 90%;
    margin: 30px auto;
    border-radius: 10px;
    border: 1px $main-color;

    a{
      position: relative;
      padding: 0 20px;
      margin: 10px;

      &:after{
        content: "";
        display: block;
        height: 2px;
        background: -webkit-linear-gradient(to right, rgba(246, 203, 255,1), $main-color);
        background: linear-gradient(to right, rgba(246, 203, 255,1), $main-color);
      }
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
}

/* PC */
@media screen and (min-width:481px){
  /*  全体　*/
  .rank{
    width: 90%;
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

}

</style>
