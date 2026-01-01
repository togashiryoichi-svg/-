<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<title>新年おみくじ</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
body {
  font-family: "Hiragino Kaku Gothic ProN", sans-serif;
  background: #fff7e6;
  text-align: center;
  padding: 20px;
}
button {
  font-size: 1.2em;
  padding: 12px 24px;
  background: #e53935;
  color: white;
  border: none;
  border-radius: 10px;
}
.card {
  background: white;
  border-radius: 12px;
  padding: 20px;
  margin-top: 20px;
}
h2 { color: #d32f2f; }
</style>
</head>

<body>

<h1>🎍 新年おみくじ 🎍</h1>
<button onclick="draw()">おみくじを引く</button>

<div id="result"></div>

<script>
const fortunes = [
  {name:"大吉", weight:40},
  {name:"中吉", weight:35},
  {name:"小吉", weight:20},
  {name:"末吉", weight:5}
];

function pickWeighted(list){
  let sum = list.reduce((a,b)=>a+b.weight,0);
  let r = Math.random()*sum;
  for(let item of list){
    if(r < item.weight) return item.name;
    r -= item.weight;
  }
}

const advice = {
学習:[
"失敗から学ぶ力が、確実に伸びています。",
"積み重ねた努力が、あとから形になります。",
"分からないことに気づけるのは、大きな強みです。",
"集中する時間をつくると、成果が出やすくなります。",
"今日の一歩が、未来につながっています。"
],
学校:[
"小さな気配りが、クラスを支えています。",
"言葉を選んで伝える力が伸びています。",
"あなたの存在が、集団を安定させています。",
"違いを受け入れる心が成長しています。",
"落ち着いた行動が、信頼につながります。"
],
家庭:[
"感謝を言葉にする力が身についています。",
"生活のリズムを意識できています。",
"家庭での行動が、学校生活にも良い影響を与えます。",
"努力を見守ってくれる人がそばにいます。",
"身の回りを整える意識が高まっています。"
],
運動:[
"続ける力が、確実に身についています。",
"努力が結果に結びつく時期です。",
"楽しむ気持ちが、力を引き出します。",
"昨日の自分を超えようとしています。",
"基礎を大切にする姿勢が力になります。"
],
お金:[
"物を大切に扱う意識が育っています。",
"考えて使う力が身についています。",
"選択に責任をもつ姿勢があります。",
"我慢する力が、将来の力になります。",
"大切にする心が、生活を安定させます。"
]
};

function rand(arr){ return arr[Math.floor(Math.random()*arr.length)]; }

function draw(){
  const result = `
  <div class="card">
    <h2>${pickWeighted(fortunes)}</h2>
    <p>📘 学習：${rand(advice.学習)}</p>
    <p>🏫 学校：${rand(advice.学校)}</p>
    <p>🏠 家庭：${rand(advice.家庭)}</p>
    <p>⚽ 運動：${rand(advice.運動)}</p>
    <p>💰 お金：${rand(advice.お金)}</p>
  </div>`;
  document.getElementById("result").innerHTML = result;
}
</script>

</body>
</html>
# -
