<template>
  <div id="app">
    <link href="https://fonts.googleapis.com/earlyaccess/nicomoji.css" rel="stylesheet">
    <div class = "header">
      <p class = "wf-nicomoji">#のぎまに。</p>
      <a>毎週月曜日更新！乃木坂46の握手会神対応ランキング！(流れる)</a>
    </div>
    <div class = "rank">
      <p class = "wf-nicomoji">こんしゅうのランキング</p>
      <div class="prof">
        <a class = "rank-top">１位  山下美月</a><br>
        <img src = "https://48pedia.org/images/8/87/2018%E5%B9%B4%E4%B9%83%E6%9C%A8%E5%9D%8246%E3%83%97%E3%83%AD%E3%83%95%E3%82%A3%E3%83%BC%E3%83%AB_%E5%B1%B1%E4%B8%8B%E7%BE%8E%E6%9C%88_2.jpg" alt="山下美月">
      </div>
      <div class = "prof ppl">
        <a class = "rank-top">２位　秋元真夏</a><br>
        <img src = "https://48pedia.org/images/8/85/2018%E5%B9%B4%E4%B9%83%E6%9C%A8%E5%9D%8246%E3%83%97%E3%83%AD%E3%83%95%E3%82%A3%E3%83%BC%E3%83%AB_%E7%A7%8B%E5%85%83%E7%9C%9F%E5%A4%8F_2.jpg" alt="秋元真夏">
      </div>
      <div class="prof">
        <a class = "rank-top">３位　山下美月</a><br>
        <img src = "https://48pedia.org/images/8/87/2018%E5%B9%B4%E4%B9%83%E6%9C%A8%E5%9D%8246%E3%83%97%E3%83%AD%E3%83%95%E3%82%A3%E3%83%BC%E3%83%AB_%E5%B1%B1%E4%B8%8B%E7%BE%8E%E6%9C%88_2.jpg" alt="山下美月">
      </div>
      <div class = "prof ppl">
        <a>４位  木村みゆき</a><br>
      </div>
      <div class = "prof">
        <a>５位  みゆき木村</a><br>
      </div>
      <div class = "prof ppl">
        <a>６位  みゆき</a><br>
      </div>
      <div class = "prof">
        <a>７位  あられ</a><br>
      </div>
      <div class = "prof ppl">
        <a>８位  お腹痛い</a><br>
      </div>
      <div class = "prof">
        <a>９位  ダム</a><br>
      </div>
      <div class = "prof ppl">
        <a>１０位  カラオケ</a><br>
      </div>
      <a>もっとみる▼</a>
    </div>
    <div class = "footer">
      <a>ページトップへ</a><br>
      <a><small>copyright</small> みゆき</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App'
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
.header .wf-nicomoji {
  font-family: "Nico Moji";
  font-size: 75px;
  color: rgba(215, 47, 252, 1);
  margin-left: 9.4px;
}

.header p{
  margin: 0px;
}

/* ランキングのとこ */
.rank{
  width: 90%;
  margin: 30px auto;
  border-radius: 10px;
  border: 1px solid rgba(215, 47, 252, 1);
}

.rank a {
  font-size: 25px;
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

.prof img{
  width: 50%;
  height: auto;
  margin-bottom: 10px;
}

.ppl{
  background-color: rgba(215, 47, 252, 0.1);
}

/* フッター */
.footer{
  height: 50px;
  background-color: rgba(215, 47, 252, 1);
  bottom: 0;
}


</style>
