# Date-Invitation
<约会邀请>
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
font-family:"Microsoft YaHei",sans-serif;
}


body{

min-height:100vh;
background:linear-gradient(135deg,#ffe5ec,#fff5f7);
display:flex;
justify-content:center;
align-items:center;
overflow:hidden;

}



.container{

width:92%;
max-width:420px;
background:white;
padding:30px;
border-radius:28px;
box-shadow:0 15px 40px rgba(0,0,0,.12);

}



h1{

text-align:center;
color:#ff4d6d;
margin-bottom:25px;

}



.title{

font-size:16px;
color:#555;
margin:18px 0 10px;

}




input{

width:100%;
padding:12px;
border-radius:15px;
border:1px solid #ddd;
font-size:16px;

}




.options{

display:flex;
flex-wrap:wrap;
gap:10px;

}




.option{

padding:10px 15px;
background:#fff0f3;
border-radius:20px;
color:#666;
cursor:pointer;
transition:.3s;

}



.option.active{

background:#ff4d6d;
color:white;
transform:scale(1.05);

}





#create{

width:100%;
margin-top:30px;
padding:15px;
border:none;
border-radius:30px;
background:#ff4d6d;
color:white;
font-size:18px;

}





.invitation{

display:none;
text-align:center;

}





.card{

background:#fff5f7;
padding:22px;
border-radius:20px;
line-height:2;
text-align:left;
margin:20px 0;

}





.card span{

color:#ff4d6d;
font-weight:bold;

}





.message{

color:#666;
line-height:1.8;

}





.btn{

border:none;
padding:13px 30px;
border-radius:30px;
font-size:17px;
margin:10px;
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





.success{

display:none;
color:#ff4d6d;
font-size:22px;
margin-top:20px;

}





.heart{

position:fixed;
animation:fall 5s linear forwards;

}





@keyframes fall{

from{

transform:translateY(-50px);
opacity:1;

}


to{

transform:translateY(100vh);
opacity:0;

}

}


</style>


</head>


<body>



<div class="container">


<div id="selectPage">


<h1>
💌 制作约会邀请
</h1>



<div class="title">
📅 选择日期
</div>


<input type="date" id="date">



<div class="title">
⏰ 选择时间
</div>


<div class="options" id="timeBox">

<div class="option">14:00</div>
<div class="option">15:00</div>
<div class="option">16:00</div>
<div class="option">18:00</div>
<div class="option">19:00</div>
<div class="option">20:00</div>
<div class="option">21:00</div>

</div>



<div class="title">
📍 选择地点
</div>


<div class="options" id="placeBox">

<div class="option">🍲 火锅店</div>
<div class="option">🥩 西餐厅</div>
<div class="option">🍣 日料店</div>
<div class="option">☕ 咖啡厅</div>
<div class="option">🎬 电影院</div>
<div class="option">🌊 江边散步</div>
<div class="option">🌳 公园</div>
<div class="option">🛍 商场</div>

</div>



<div class="title">
💕 约会内容
</div>


<div class="options" id="contentBox">

<div class="option">一起吃饭聊天</div>
<div class="option">看电影</div>
<div class="option">散步吹风</div>
<div class="option">喝咖啡</div>
<div class="option">看夜景</div>
<div class="option">逛街</div>
<div class="option">拍照打卡</div>

</div>



<button id="create">
生成邀请 ❤️
</button>


</div><!-- 邀请展示页面 -->

<div id="invitePage" class="invitation">


<h1>
💌 给你的一份邀请
</h1>



<div class="card">


📅 时间：
<br>

<span id="showDate"></span>



<br><br>


📍 地点：
<br>

<span id="showPlace"></span>



<br><br>


💕 计划：
<br>

<span id="showContent"></span>



</div>




<div class="message">

希望这一天<br>
可以成为一个开心的回忆 ❤️

</div>




<button class="btn" id="yes">

接受 ❤️

</button>



<button class="btn" id="no">

拒绝 😢

</button>



<div class="success" id="success">

🎉 邀请成功！<br>
期待与你见面～

</div>



</div>



</div>





<script>


// =====================
// 选项点击
// =====================


function choose(boxId){


let box=document.getElementById(boxId);

let items=box.querySelectorAll(".option");


items.forEach(item=>{


item.onclick=function(){


items.forEach(i=>{

i.classList.remove("active");

});


this.classList.add("active");


}


});


}



choose("timeBox");

choose("placeBox");

choose("contentBox");





// =====================
// 生成邀请
// =====================


document.getElementById("create").onclick=function(){



let date=document.getElementById("date").value;


let time=document.querySelector("#timeBox .active");


let place=document.querySelector("#placeBox .active");


let content=document.querySelector("#contentBox .active");





if(!date || !time || !place || !content){


alert("请把约会信息选择完整哦 ❤️");

return;


}




let dateText=date.split("-")[0]+"年"+
date.split("-")[1]+"月"+
date.split("-")[2]+"日";




document.getElementById("showDate").innerHTML=

dateText+" "+time.innerHTML;




document.getElementById("showPlace").innerHTML=

place.innerHTML;




document.getElementById("showContent").innerHTML=

content.innerHTML;





document.getElementById("selectPage").style.display="none";


document.getElementById("invitePage").style.display="block";



}






// =====================
// 拒绝按钮逃跑
// =====================


let no=document.getElementById("no");



function runAway(){


let x=Math.random()*260;

let y=Math.random()*450;



no.style.left=x+"px";

no.style.top=y+"px";


}



no.onmouseenter=runAway;


no.onclick=runAway;






// =====================
// 接受按钮
// =====================


document.getElementById("yes").onclick=function(){



document.getElementById("success").style.display="block";


this.innerHTML="已经约好了 ❤️";


no.style.display="none";



}







// =====================
// 飘落爱心
// =====================


setInterval(function(){


let heart=document.createElement("div");


heart.className="heart";


heart.innerHTML="❤️";


heart.style.left=Math.random()*100+"vw";


heart.style.fontSize=
(15+Math.random()*25)+"px";



document.body.appendChild(heart);



setTimeout(()=>{


heart.remove();


},5000);



},800);



</script>



</body>

</html>
