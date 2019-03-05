<template>
  <div id="app">
    <link href="https://fonts.googleapis.com/earlyaccess/nicomoji.css" rel="stylesheet">
    <header>
      <p class = "wf-nicomoji">#のぎまに。</p>
      <a>毎週月曜日更新！乃木坂46の握手会神対応ランキング！(流れる)</a>
      <p id = "search">推しの順位は？<input type = "text"　size = "15" value = "例:白石麻衣"><input type = "submit" value = "検索"></p>
    </header>

    <div class = "rank">
      <p class = "wf-nicomoji">こんしゅうのランキング</p>

      <div v-for = "data in sample_data">
        <div v-if = "data.rank <= 3">
          <div class="prof">
            <a class = "rank-top">{{ data.rank }}位  {{ data.name }}</a><br>
            <img src = "images/山下美月.jpg" alt = "山下美月">
          </div>
        </div>
        <div v-else>
          <div class = "prof">
            <a>{{ data.rank }}位  {{ data.name }}</a><br>
          </div>
        </div>
      </div>

      <a>もっとみる▼</a>
    </div>

    <footer>
      <a>ページトップへ</a><br>
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
      results: [],
      sample_data: [
        {name:"秋元真夏", score:"2.4", tweet:"可愛い", date:"2019-3-5", rank:"1"},
        {name:"山下美月", score:"2.4", tweet:"可愛い", date:"2019-3-5", rank:"2"},
        {name:"梅澤美波", score:"2.4", tweet:"可愛い", date:"2019-3-5", rank:"3"},
        {name:"白石麻衣", score:"2.4", tweet:"可愛い", date:"2019-3-5", rank:"4"},
        {name:"秋元真夏", score:"2.4", tweet:"可愛い", date:"2019-3-5", rank:"5"},
        {name:"秋元真夏", score:"2.4", tweet:"可愛い", date:"2019-3-5", rank:"6"},
        {name:"秋元真夏", score:"2.4", tweet:"可愛い", date:"2019-3-5", rank:"7"},
        {name:"秋元真夏", score:"2.4", tweet:"可愛い", date:"2019-3-5", rank:"8"},
        {name:"秋元真夏", score:"2.4", tweet:"可愛い", date:"2019-3-5", rank:"9"},
        {name:"秋元真夏", score:"2.4", tweet:"可愛い", date:"2019-3-5", rank:"10"}
      ]
    }
  },
  mounted(){
    axios.get('http://localhost:5000/results')
    .then((res) => {
      console.log(res.data)
      this.results = res.data
    })
    .catch()
  }
}
</script>

<style>
/*  全体　*/
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  width: auto;
  margin: 0px;
}

a{
  display: inline-block;
}

/* ヘッダー */
header .wf-nicomoji {
  font-family: "Nico Moji";
  font-size: 75px;
  color: rgba(215, 47, 252, 1);
  margin-left: 9.4px;
}

header p{
  margin: 0px;
}

header #search{
  background: rgba(215, 47, 252, 1);
}

/* ランキングのとこ */
.rank{
  width: 90%;
  margin: 30px auto;
  border-radius: 10px;
  border: 1px solid rgba(215, 47, 252, 1);
}

.rank a {
  position: relative;
  padding: 0 20px;
  margin: 10px;
}
.rank a:after {
  content: "";
  display: block;
  height: 2px;
  background: -webkit-linear-gradient(to right, rgba(246, 203, 255,1), rgba(215, 47, 252, 1));
  background: linear-gradient(to right, rgba(246, 203, 255,1), rgba(215, 47, 252, 1));
}

.rank .wf-nicomoji{
  font-family: "Nico Moji";
  font-size: 33px;
  background-color: rgba(215, 47, 252, 1);
  border-top-left-radius: 9px;
  border-top-right-radius: 9px;
  color: rgba(255, 255, 255, 1);
  margin: 0;
  padding: 5px;
}

.rank .prof img{
  width: 50%;
  height: auto;
  margin-bottom: 10px;
}

.ppl{
  background-color: rgba(215, 47, 252, 0.1);
}

/* フッター */
footer{
  height: 50px;
  background-color: rgba(215, 47, 252, 1);
  bottom: 0;
}

</style>
