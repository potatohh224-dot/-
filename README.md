# -
あなたの恋愛感覚をサッカー選手に例えます！
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>バンビ診断テスト</title>
<style>
body {
  font-family: sans-serif;
  text-align: center;
  padding: 20px;
  background: linear-gradient(135deg, #ff7eb3, #ff758c, #ffb199);
  color: white;
}

.container {
  background: rgba(255,255,255,0.1);
  padding: 20px;
  border-radius: 20px;
  backdrop-filter: blur(10px);
}

button {
  margin: 10px;
  padding: 12px 20px;
  font-size: 15px;
  border-radius: 20px;
  border: none;
  background: white;
  color: black;
  cursor: pointer;
}

input {
  padding: 10px;
  border-radius: 10px;
  border: none;
  margin: 10px;
}

h1 {
  font-size: 28px;
}
</style>
</head>
<body>

<div class="container">

<h1>💘バンビ診断テスト</h1>

<div id="start">
<p>名前を入力してね👇</p>
<input id="nameInput" placeholder="名前">
<br>
<button onclick="startTest()">診断スタート</button>
</div>

<p id="question"></p>
<div id="choices"></div>

</div>

<script>
let userName = "";

function startTest(){
  userName = document.getElementById("nameInput").value || "あなた";
  document.getElementById("start").style.display = "none";
  showQuestion();
}

let questions = [
{q:"好きな人が30m先から来る！",a:[{text:"全力で手振る",type:"KANE"},{text:"気づかないフリ",type:"NEUER"}]},
{q:"LINEが来た！",a:[{text:"即返信",type:"MBAPPE"},{text:"様子見る",type:"SOMMER"}]},
{q:"デートで服ダサい",a:[{text:"褒める",type:"MODRIC"},{text:"正直に言う",type:"RAMOS"}]},
{q:"目が合った",a:[{text:"笑う",type:"MESSI"},{text:"逸らす",type:"LUKAKU"}]},
{q:"恋愛スタイル",a:[{text:"勢い",type:"HAALAND"},{text:"戦略",type:"MODRIC"}]},
{q:"嫉妬したら",a:[{text:"出る",type:"RAMOS"},{text:"隠す",type:"VVD"}]},
{q:"距離の詰め方",a:[{text:"一気",type:"DAVIES"},{text:"慎重",type:"SOMMER"}]},
{q:"モテ方",a:[{text:"無自覚",type:"MESSI"},{text:"計算",type:"OLISE"}]},
{q:"恋愛中",a:[{text:"テンション高い",type:"MULLER"},{text:"冷静",type:"SOMMER"}]},
{q:"告白",a:[{text:"直感",type:"MBAPPE"},{text:"タイミング",type:"MODRIC"}]},
{q:"ライバル",a:[{text:"潰す",type:"RUDIGER"},{text:"様子見",type:"VVD"}]},
{q:"武器",a:[{text:"魅力",type:"MUSIALA"},{text:"強気",type:"IBRA"}]},
{q:"やりがち",a:[{text:"突っ走る",type:"HAALAND"},{text:"ズレる",type:"LUKAKU"}]},
{q:"好きな人の前",a:[{text:"天然",type:"KUBO"},{text:"魅せる",type:"YAMAL"}]},
{q:"最終的に",a:[{text:"動く",type:"KANE"},{text:"迷う",type:"VAR"}]}
];

let score = {};
let current = 0;

function answer(type){
score[type] = (score[type] || 0) + 1;
current++;
if(current < questions.length){
showQuestion();
}else{
showResult();
}
}

function showQuestion(){
let q = questions[current];
document.getElementById("question").innerText = q.q;

let html="";
q.a.forEach(c=>{
html += `<button onclick="answer('${c.type}')">${c.text}</button>`;
});
document.getElementById("choices").innerHTML = html;
}

function showResult(){
let resultType = Object.keys(score).reduce((a,b)=> score[a]>score[b]?a:b);

let results = {
KANE:"ゴール量産機タイプ",
MBAPPE:"爆速カウンタータイプ",
MESSI:"理不尽モテタイプ",
HAALAND:"ゴリ押し怪獣タイプ",
MODRIC:"恋の司令塔タイプ",
MUSIALA:"魔法使いタイプ",
OLISE:"メロドリブラータイプ",
MULLER:"猪突猛進タイプ",
NEUER:"鉄壁ガードタイプ",
KUBO:"天然人たらしタイプ",
SOMMER:"冷静沈着タイプ",
DAVIES:"爆速距離詰めタイプ",
VVD:"高嶺の花タイプ",
RAMOS:"重すぎ恋愛タイプ",
RUDIGER:"圧強すぎタイプ",
LUKAKU:"ズレ恋愛タイプ",
IBRA:"厨二王タイプ",
YAMAL:"魅せ恋愛タイプ",
VAR:"迷子恋愛タイプ"
};

document.body.innerHTML = `
<h1>${userName}の診断結果💘</h1>
<h2>${results[resultType]}</h2>
<p>※当たってなくても責任は取りません😇</p>
`;
}

</script>

</body>
</html>
