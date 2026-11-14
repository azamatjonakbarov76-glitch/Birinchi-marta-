<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Kalkulyator</title>
<style>
*{box-sizing:border-box;margin:0}
body{min-height:100vh;display:flex;align-items:center;justify-content:center;background:#1b1f2a;font-family:system-ui,sans-serif}
.calc{width:320px;padding:16px;background:#262b3a;border-radius:20px}
#ekran{height:90px;margin-bottom:14px;padding:12px;border-radius:12px;background:#12151d;color:#fff;font-size:40px;overflow:hidden;display:flex;align-items:flex-end;justify-content:flex-end}
.t{display:grid;grid-template-columns:repeat(4,1fr);gap:10px}
button{height:64px;border:0;border-radius:12px;font-size:24px;background:#3a4157;color:#fff}
button:active{filter:brightness(1.3)}
.a{background:#f0a030;color:#1b1f2a}
.c{background:#d9534f}
.n{grid-column:span 2}
</style>
</head>
<body>
<div class="calc">
<div id="ekran">0</div>
<div class="t">
<button class="c" onclick="tozala()">C</button>
<button onclick="ochir()">⌫</button>
<button class="a" onclick="yoz('%')">%</button>
<button class="a" onclick="yoz('/')">÷</button>
<button onclick="yoz('7')">7</button>
<button onclick="yoz('8')">8</button>
<button onclick="yoz('9')">9</button>
<button class="a" onclick="yoz('*')">×</button>
<button onclick="yoz('4')">4</button>
<button onclick="yoz('5')">5</button>
<button onclick="yoz('6')">6</button>
<button class="a" onclick="yoz('-')">−</button>
<button onclick="yoz('1')">1</button>
<button onclick="yoz('2')">2</button>
<button onclick="yoz('3')">3</button>
<button class="a" onclick="yoz('+')">+</button>
<button class="n" onclick="yoz('0')">0</button>
<button onclick="yoz('.')">.</button>
<button class="a" onclick="hisobla()">=</button>
</div>
</div>
<script>
let f='';
const e=document.getElementById('ekran');
function k(){e.textContent=(f||'0').replace(/\*/g,'×').replace(/\//g,'÷')}
function yoz(b){f+=b;k()}
function tozala(){f='';k()}
function ochir(){f=f.slice(0,-1);k()}
function hisobla(){
try{
if(!/^[0-9+\-*/%.() ]+$/.test(f))return;
const r=Function('"use strict";return ('+f.replace(/%/g,'/100')+')')();
f=String(Math.round(r*1e10)/1e10)
}catch(x){f='';e.textContent='Xato';return}
k()
}
</script>
</body>
</html>