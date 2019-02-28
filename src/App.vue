<template>
  <div id="app">
    <link href="https://fonts.googleapis.com/earlyaccess/nicomoji.css" rel="stylesheet">
    <div class = "head">
      <p class = "wf-nicomoji">のぎまに。</p>
      <a>毎週月曜日更新！乃木坂46の握手会神対応ランキング！(流れる)</a>
    </div>
    <div class = "rank">
      <a id = "title" class = "wf-nicomoji">こんしゅうのランキング</a><br>
      <a class = "rank-top"><span class = "bignum">１</span>山本美月</a><br>
      <a class = "rank-top"><span class = "bignum">２</span>秋元真夏</a><br>
      <a class = "rank-top"><span class = "bignum">３</span>あああああ</a><br>
      <a><span class = "num">４</span>よんい</a><br>
      <a><span class = "num">５</span>ごい</a><br>
      <a>もっとみる</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: rgba(215, 47, 252, 1);
  width: auto;
  height: 800px;
  padding: 0px 10px;
}

a{
  display: inline-block;
}
.head .wf-nicomoji {
  font-family: "Nico Moji";
  font-size: 80px;
  color: #ffffff;
  margin-left: 13px;
}

.head p{
  margin: 0px;

}

.rank{
  width: 90%;
  background-color: #ffffff;
  margin: 30px auto;
  border-radius: 10px;
  border: 3px solid rgb(59, 130, 0);
}

.rank a{
  margin: 5px;
}

.rank .bignum{
  background-color: rgb(59, 130, 0);
  border-radius: 50%;
  color: #ffffff;
  padding: 5px;
  font-size: 20px;
}

.rank .wf-nicomoji{
  font-family: "Nico Moji";
  font-size: 33px;
}

.rank #title{
  /* border-bottom: 1px dashed rgb(59, 130, 0); */
  color: rgb(59, 130, 0);
  margin: 10px 0;
}
.rank .num{
  color: rgb(59, 130, 0);

}

.rank .rank-top{
  font-size: 25px;
}


</style>
