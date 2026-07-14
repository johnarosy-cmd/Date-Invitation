# Date-Invitation
<来自牛牛的约会邀请>
<html lang="zh-CN">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>约会选择器</title>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:"Microsoft YaHei",sans-serif;
}


body{

min-height:100vh;
background:linear-gradient(135deg,#ffe0e8,#fff7f8);
display:flex;
justify-content:center;
align-items:center;

}



.box{

width:92%;
max-width:420px;
background:white;
border-radius:30px;
padding:30px;
box-shadow:0 15px 40px rgba(0,0,0,.12);
text-align:center;

}




h1{

color:#ff4d6d;
font-size:27px;
margin-bottom:20px;

}




p{

color:#777;
line-height:1.8;

}





.page{

display:none;

}


.page.active{

display:block;

}





.start-btn,
.submit-btn{


width:100%;
padding:15px;
margin-top:30px;

border:none;
border-radius:30px;

background:#ff4d6d;
color:white;

font-size:18px;

}





.title{

font-size:18px;
margin:20px 0 15px;
color:#555;

}





input[type=date]{


width:100%;
padding:12px;

border-radius:15px;

border:1px solid #ddd;

font-size:16px;

}





.options{


display:flex;
flex-wrap:wrap;
gap:12px;

}





.option{


padding:12px 16px;

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





.card{


background:#fff5f7;

padding:22px;

border-radius:20px;

text-align:left;

line-height:2;

margin-top:20px;


}





.card span{


color:#ff4d6d;

font-weight:bold;


}





.back-text{

margin-top:20px;

color:#999;

font-size:14px;

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



.success{


display:none;

color:#ff4d6d;

font-size:22px;

margin-top:20px;

}




</style>


</head>


<body>



<div class="box">



<!-- 第一页 -->

<div class="page active" id="page1">


<h1>
💌 有一个小邀请给你
</h1>


<p>

这一次<br>

想把约会的选择权交给你 ❤️

<br><br>

希望我们可以一起<br>

度过一段开心的时间

</p>



<button class="start-btn" onclick="nextPage(2)">

开始选择 ❤️

</button>


</div>





<!-- 第二页 日期 -->


<div class="page" id="page2">


<h1>
📅 选择日期
</h1>


<input type="date" id="date">


<button class="start-btn" onclick="nextPage(3)">

下一步

</button>


</div>





<!-- 第三页 时间 -->


<div class="page" id="page3">


<h1>
⏰ 选择时间
</h1>


<div class="options" id="time">


<div class="option">14:00</div>
<div class="option">15:00</div>
<div class="option">16:00</div>
<div class="option">18:00</div>
<div class="option">19:00</div>
<div class="option">20:00</div>
<div class="option">21:00</div>


</div>



<button class="start-btn" onclick="nextPage(4)">

下一步

</button>


</div><!-- 第四页 地点 -->

<div class="page" id="page4">

<h1>
📍 选择地点
</h1>


<div class="options" id="place">


<div class="option">🍲 火锅店</div>

<div class="option">🥩 西餐厅</div>

<div class="option">🍣 日料店</div>

<div class="option">☕ 咖啡厅</div>

<div class="option">🎬 电影院</div>

<div class="option">🌊 江边散步</div>

<div class="option">🌳 公园</div>

<div class="option">🛍 商场</div>


</div>



<button class="start-btn" onclick="nextPage(5)">

下一步

</button>


</div>





<!-- 第五页 内容 -->


<div class="page" id="page5">


<h1>
💕 想怎么度过
</h1>


<div class="options" id="content">


<div class="option">一起吃饭聊天</div>

<div class="option">看电影</div>

<div class="option">散步吹风</div>

<div class="option">喝咖啡</div>

<div class="option">看夜景</div>

<div class="option">逛街</div>

<div class="option">拍照打卡</div>


</div>



<button class="submit-btn" onclick="submitForm()">

发送给他 ❤️

</button>



</div>






<!-- 第六页结果 -->


<div class="page" id="page6">


<h1>
🎉 收到你的约会计划
</h1>



<div class="card">


📅 日期：

<br>

<span id="resultDate"></span>


<br><br>


⏰ 时间：

<br>

<span id="resultTime"></span>


<br><br>


📍 地点：

<br>

<span id="resultPlace"></span>


<br><br>


💕 安排：

<br>

<span id="resultContent"></span>


</div>



<p>

期待与你见面 ❤️

</p>



<div class="success" id="success">


你的选择已经发送给他啦～

</div>



</div>






</div>





<script>



// 页面切换


function nextPage(num){


document.querySelectorAll(".page")
.forEach(p=>{

p.classList.remove("active");

});


document.getElementById("page"+num)
.classList.add("active");


}







// 选项选择


function choose(id){


let box=document.getElementById(id);


let options=box.querySelectorAll(".option");



options.forEach(item=>{


item.onclick=function(){


options.forEach(o=>{

o.classList.remove("active");

});


this.classList.add("active");


}


});


}



choose("time");

choose("place");

choose("content");









// 提交


function submitForm(){



let date=document.getElementById("date").value;


let time=document.querySelector("#time .active");


let place=document.querySelector("#place .active");


let content=document.querySelector("#content .active");



if(!date || !time || !place || !content){


alert("请完成所有选择 ❤️");

return;


}





// 显示结果


document.getElementById("resultDate").innerHTML=date;


document.getElementById("resultTime").innerHTML=time.innerHTML;


document.getElementById("resultPlace").innerHTML=place.innerHTML;


document.getElementById("resultContent").innerHTML=content.innerHTML;



nextPage(6);



document.getElementById("success").style.display="block";





function submitForm(){


let date=document.getElementById("date").value;

let time=document.querySelector("#time .active");

let place=document.querySelector("#place .active");

let content=document.querySelector("#content .active");


if(!date || !time || !place || !content){

alert("请完成所有选择 ❤️");

return;

}



let formData=new FormData();


formData.append(
"日期",
date
);


formData.append(
"时间",
time.innerHTML
);


formData.append(
"地点",
place.innerHTML
);


formData.append(
"约会内容",
content.innerHTML
);





fetch(
"https://formspree.io/f/mojgvkny",
{
method:"POST",
body:formData,
headers:{
"Accept":"application/json"
}
}
)
.then(response=>{

if(response.ok){

console.log("发送成功");

}else{

console.log("发送失败");

}

})
.catch(error=>{

console.log(error);

});

.then(()=>{


document.getElementById("resultDate").innerHTML=date;


document.getElementById("resultTime").innerHTML=time.innerHTML;


document.getElementById("resultPlace").innerHTML=place.innerHTML;


document.getElementById("resultContent").innerHTML=content.innerHTML;



nextPage(6);



})

.catch(()=>{


alert("发送失败，请稍后再试");


});



}

}








// 爱心动画


setInterval(()=>{


let heart=document.createElement("div");


heart.className="heart";

heart.innerHTML="❤️";


heart.style.left=Math.random()*100+"vw";


heart.style.fontSize=
(15+Math.random()*20)+"px";


document.body.appendChild(heart);



setTimeout(()=>{

heart.remove();

},5000);



},800);



</script>



</body>

</html>
