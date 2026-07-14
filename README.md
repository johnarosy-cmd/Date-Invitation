# Date-Invitation
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>约会邀请</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:"Microsoft YaHei";
}

body{
    height:100vh;
    background:linear-gradient(135deg,#ffafbd,#ffc3a0);
    display:flex;
    justify-content:center;
    align-items:center;
    overflow:hidden;
}


.card{

    width:90%;
    max-width:400px;
    background:white;
    padding:35px 25px;
    border-radius:25px;
    text-align:center;
    box-shadow:0 15px 40px rgba(0,0,0,.15);

}


h1{

color:#ff4d6d;
margin-bottom:20px;

}


.info{

background:#fff5f7;
padding:20px;
border-radius:15px;
text-align:left;
line-height:2;
margin-bottom:25px;

}


button{

padding:12px 30px;
border:none;
border-radius:30px;
font-size:17px;
cursor:pointer;

}


#yes{

background:#ff4d6d;
color:white;

}


#no{

background:#eee;
color:#777;
position:absolute;

}


#result{

display:none;
margin-top:25px;
color:#ff4d6d;
font-size:20px;

}


</style>

</head>


<body>


<div class="card">


<h1>💌 约会邀请函</h1>


<div class="info">

📅 时间：
<span id="time"></span>
<br>

📍 地点：
<span id="place"></span>

<br>

💕 计划：
<span id="plan"></span>

</div>


<p>
希望这一天<br>
可以和你一起留下一个开心的回忆
</p>


<br>


<button id="yes">
接受 ❤️
</button>


<button id="no">
拒绝 😢
</button>


<div id="result">

🎉 邀请成功！<br>
期待与你见面～

</div>


</div>



<script>


// ====== 在这里修改你的约会内容 ======

let dateTime="2026年7月20日 18:30";

let place="XX餐厅";

let plan="一起吃饭，看电影，散步聊天";


// ==================================



document.getElementById("time").innerHTML=dateTime;

document.getElementById("place").innerHTML=place;

document.getElementById("plan").innerHTML=plan;




let no=document.getElementById("no");


// 鼠标靠近逃跑

no.onmouseenter=function(){

moveNo();

}


// 点击逃跑

no.onclick=function(){

moveNo();

}



function moveNo(){

let x=Math.random()*250;

let y=Math.random()*400;


no.style.left=x+"px";

no.style.top=y+"px";


}




document.getElementById("yes").onclick=function(){


document.getElementById("result").style.display="block";


no.style.display="none";


this.innerHTML="已经约好了 ❤️";


}




</script>


</body>

</html>
