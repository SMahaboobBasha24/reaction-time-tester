<!DOCTYPE html>
<html>
<head>
<title>Reaction Time Tester</title>

<style>

body{
font-family:Arial;
display:flex;
justify-content:center;
align-items:center;
height:100vh;
margin:0;
background:#0f172a;
color:white;
}

#box{
width:300px;
height:200px;
display:flex;
justify-content:center;
align-items:center;
border-radius:10px;
background:#334155;
cursor:pointer;
text-align:center;
}

</style>

</head>

<body>

<div id="box" onclick="handleClick()">
Click to Start
</div>

<script>

let startTime, timeout
let state = "idle"

function handleClick(){

let box = document.getElementById("box")

if(state === "idle"){

box.innerText = "Wait..."
box.style.background = "#f59e0b"

timeout = setTimeout(()=>{

box.innerText = "CLICK NOW!"
box.style.background = "#22c55e"

startTime = new Date().getTime()
state = "ready"

}, Math.random()*3000 + 1000)

state = "waiting"

}

else if(state === "waiting"){

clearTimeout(timeout)

box.innerText = "Too Soon ❌"
box.style.background = "#ef4444"

state = "idle"

}

else if(state === "ready"){

let reactionTime = new Date().getTime() - startTime

box.innerText = "Time: " + reactionTime + " ms\nClick to try again"
box.style.background = "#334155"

state = "idle"

}

}

</script>

</body>
</html>
