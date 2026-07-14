# Date-Invitation
约会邀请
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>约会邀请生成器</title>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:"Microsoft YaHei";
}

body{
height:100vh;
background:linear-gradient(135deg,#ff9a9e,#fad0c4);
display:flex;
justify-content:center;
align-items:center;
overflow:hidden;
}


.box{
width:90%;
max-width:420px;
background:white;
padding:30px;
border-radius:25px;
box-shadow:0 10px 30px #9995;
text-align:center;
}


h1{
color:#ff4d6d;
margin-bottom:20px;
}


input,textarea{

width:100%;
padding:12px;
margin:8px 0;
border-radius:12px;
border:1px solid #ddd;
font-size:15px;

}


textarea{
height:80px;
resize:none;
}


button{

padding:12px 25px;
border:none;
border-radius:30px;
font-size:16px;
margin-top:15px;
cursor:pointer;

}


#create{

background:#ff4d6d;
color:white;

}


.invite{

display:none;

}


.card{

background:#fff5f7;
padding:20px;
border-radius:15px;
line-height:2;
margin-top:20px;

}


#yes{

background:#ff4d6d;
color:white;

}


#no{

background:#eee;
position:absolute;

}


#success{

display:none;
color:#ff4d6d;
font-size:20px;
margin-top:20px;

}


</style>

</head>


<body>


<div class="box">


<div id="edit">

<h1>💌 制作约会邀请</h1>


<input id="time" placeholder="输入时间，例如：周六晚上7点">


<input id="place" placeholder="输入地点，例如：XX餐厅">


<textarea id="content" placeholder="输入约会内容，例如：吃饭、看电影、散步"></textarea>


<button id="create">
生成邀请 ❤️
</button>


</div>



<div id="invite">


<h1>💌 给你的邀请</h1>


<div class="card">

📅 时间：
<div id="showTime"></div>


📍 地点：
<div id="showPlace"></div>


💕 计划：
<div id="showContent"></div>


</div>


<p style="margin-top:20px">
希望今天能成为一个开心的回忆
</p>


<button id="yes">
接受 ❤️
</button>


<button id="no">
拒绝 😢
</button>


<div id="success">

🎉 邀请成功！<br>
期待与你见面～

</div>


</div>



</div>



<script>


let create=document.getElementById("create");


create.onclick=function(){


document.getElementById("showTime").innerHTML=
document.getElementById("time").value;


document.getElementById("showPlace").innerHTML=
document.getElementById("place").value;


document.getElementById("showContent").innerHTML=
document.getElementById("content").value;



document.getElementById("edit").style.display="none";

document.getElementById("invite").style.display="block";


}



let no=document.getElementById("no");


function escape(){

let x=Math.random()*250;

let y=Math.random()*400;

no.style.left=x+"px";

no.style.top=y+"px";

}


no.onmouseenter=escape;

no.onclick=escape;



document.getElementById("yes").onclick=function(){

document.getElementById("success").style.display="block";

no.style.display="none";

this.innerHTML="已经约好了 ❤️";

}



</script>


</body>
</html>
