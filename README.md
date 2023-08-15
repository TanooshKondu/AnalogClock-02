# AnalogClock-02

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Analog Clock</title>
    <link rel="stylesheet" href="Analog-clock.css">
</head>
<body>
    <div class="container">
        <div class="clock">
            <div style="--clr:#ff3d58; --h:68px;" class="hand" id="hour"><i></i></div>
            <div style="--clr:#fcfc03; --h:86px;" class="hand" id="min"><i></i></div>
            <div style="--clr:#212121; --h:94px;" class="hand" id="sec"><i></i></div>
            <span style="--i:1;"><b>1</b></span>
            <span style="--i:2;"><b>2</b></span>
            <span style="--i:3;"><b>3</b></span>
            <span style="--i:4;"><b>4</b></span>
            <span style="--i:5;"><b>5</b></span>
            <span style="--i:6;"><b>6</b></span>
            <span style="--i:7;"><b>7</b></span>
            <span style="--i:8;"><b>8</b></span>
            <span style="--i:9;"><b>9</b></span>
            <span style="--i:10;"><b>10</b></span>
            <span style="--i:11;"><b>11</b></span>
            <span style="--i:12;"><b>12</b></span>
        </div>
    </div>
    <script src="Analog-clock.js"></script>
</body>
</html>



*{
    margin:0;
    padding:0;
    box-sizing: border-box;
    font-family:Arial, Helvetica, sans-serif;
    color: #fff;
}

body{
    display:flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background: url("https://i.imgur.com/VtKUvFq.jpg");
    background-size: cover;
}
.container{
    position: relative;
}
.clock{
    width:300px;
    height:300px;
    border-radius: 50%;
    background-color: rgba(255,255, 255, 0.1);
    border: 2px solid rgba(255, 255, 255, 1.3);
    box-shadow: 0px 0px 30px rgba(0, 0, 0, 9.6);
    display: flex;
    justify-content: center;
    align-items:center;
}
.clock span{
    position: absolute;
    transform: rotate(calc(30deg * var(--i)));
    inset: 12px;
    text-align: center;
}
.clock span b{
    transform: rotate(calc(-30deg *var(--i)));
    display: inline-block;
    font-size:20px;
    color:#212121;
}
.clock::before{
    content:'';
    position: absolute;
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background-color: #035afc;
}
.hand{
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: flex-end;
}

.hand i{
    position: absolute;
    background-color: var(--clr);
    width: 4px;
    height: var(--h);
    border-radius: 8px;
}


let hour = document.getElementById("hour");
let min = document.getElementById("min");
let sec = document.getElementById("sec");

function Time(){
    const date = new Date();

    const h = date.getHours();
    const m = date.getMinutes();
    const s = date.getSeconds();

    const hRotate = 30*h + m/2;
    const mRotate = 6*m;
    const sRotate = 6*s;

    hour.style.transform = `rotate(${hRotate}deg)`;
    min.style.transform = `rotate(${mRotate}deg)`;
    sec.style.transform = `rotate(${sRotate}deg)`;
}
setInterval(Time, 1000);
