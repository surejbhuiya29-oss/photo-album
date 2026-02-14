<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Friendship Album</title>

<style>
body{
    margin:0;
    background:linear-gradient(135deg,#1d2671,#c33764);
    display:flex;
    justify-content:center;
    align-items:center;
    height:100vh;
    overflow:hidden;
    font-family: 'Poppins', sans-serif;
}

/* BOOK FRAME */
.book{
    width:320px;
    height:420px;
    position:relative;
    perspective:2000px;
}

.page{
    width:100%;
    height:100%;
    position:absolute;
    transform-origin:left;
    transition:transform 1.2s;
    border-radius:10px;
    overflow:hidden;
    background:white;
    box-shadow:0 10px 25px rgba(0,0,0,0.6);
}

.page img{
    width:100%;
    height:100%;
    object-fit:cover;
}

/* Flip animation */
.page.flipped{
    transform:rotateY(-180deg);
}

/* Last Page Note */
.note{
    display:flex;
    justify-content:center;
    align-items:center;
    text-align:center;
    padding:20px;
    background:linear-gradient(to bottom,#ffecd2,#fcb69f);
    font-size:18px;
    font-weight:bold;
    color:#333;
}

/* Controls */
.controls{
    position:absolute;
    bottom:15px;
    text-align:center;
    width:100%;
}

button{
    padding:8px 15px;
    margin:5px;
    border:none;
    border-radius:20px;
    background:#ff4e88;
    color:white;
    font-size:14px;
}
</style>
</head>

<body>

<!-- Background Music -->
<audio id="bgm" autoplay loop>
    <source src="bgm.mp3" type="audio/mpeg">
</audio>

<div class="book" id="book">

<!-- 20 PHOTO PAGES -->
<div class="page"><img src="photo1.jpg"></div>
<div class="page"><img src="photo2.jpg"></div>
<div class="page"><img src="photo3.jpg"></div>
<div class="page"><img src="photo4.jpg"></div>
<div class="page"><img src="photo5.jpg"></div>
<div class="page"><img src="photo6.jpg"></div>
<div class="page"><img src="photo7.jpg"></div>
<div class="page"><img src="photo8.jpg"></div>
<div class="page"><img src="photo9.jpg"></div>
<div class="page"><img src="photo10.jpg"></div>
<div class="page"><img src="photo11.jpg"></div>
<div class="page"><img src="photo12.jpg"></div>
<div class="page"><img src="photo13.jpg"></div>
<div class="page"><img src="photo14.jpg"></div>
<div class="page"><img src="photo15.jpg"></div>
<div class="page"><img src="photo16.jpg"></div>
<div class="page"><img src="photo17.jpg"></div>
<div class="page"><img src="photo18.jpg"></div>
<div class="page"><img src="photo19.jpg"></div>
<div class="page"><img src="photo20.jpg"></div>

<!-- LAST PAGE NOTE -->
<div class="page note">
    💛 Dosti koi lafzon ki mohtaj nahi hoti...  
    Yeh ek ehsaas hai jo zindagi bhar saath rehta hai.  
    Thank you for being my best friend forever 💫
</div>

</div>

<div class="controls">
    <button onclick="prevPage()">⬅ Prev</button>
    <button onclick="nextPage()">Next ➡</button>
</div>

<script>
const pages = document.querySelectorAll(".page");
let current = 0;

function nextPage(){
    if(current < pages.length){
        pages[current].classList.add("flipped");
        current++;
    }
}

function prevPage(){
    if(current > 0){
        current--;
        pages[current].classList.remove("flipped");
    }
}

/* Auto Flip */
setInterval(()=>{
    if(current < pages.length){
        nextPage();
    } else {
        for(let i=pages.length-1;i>=0;i--){
            pages[i].classList.remove("flipped");
        }
        current=0;
    }
},3500);
</script>

</body>
</html>
