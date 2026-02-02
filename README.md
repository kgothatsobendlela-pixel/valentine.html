# valentine.html
valentine.html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Be My Valentine 💖</title>

<style>
    body {
        margin: 0;
        padding: 0;
        height: 100vh;
        background: linear-gradient(135deg, #ff758c, #ff7eb3);
        display: flex;
        justify-content: center;
        align-items: center;
        font-family: 'Arial', sans-serif;
        overflow: hidden;
    }

    .container {
        text-align: center;
        background: white;
        padding: 30px;
        border-radius: 20px;
        box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        max-width: 90%;
    }

    h1 {
        color: #ff4d6d;
        margin-bottom: 20px;
    }

    img {
        width: 200px;
        border-radius: 15px;
        margin-bottom: 20px;
    }

    .buttons {
        position: relative;
        height: 100px;
    }

    button {
        padding: 15px 25px;
        font-size: 18px;
        border: none;
        border-radius: 10px;
        cursor: pointer;
        transition: all 0.3s ease;
    }

    #yesBtn {
        background-color: #ff4d6d;
        color: white;
        font-size: 18px;
    }

    #noBtn {
        background-color: #ccc;
        color: #333;
        position: absolute;
        right: 0;
    }

    .celebration {
        display: none;
    }

    .hearts {
        position: fixed;
        top: -10px;
        font-size: 24px;
        animation: fall 3s linear infinite;
    }

    @keyframes fall {
        to {
            transform: translateY(110vh);
            opacity: 0;
        }
    }
</style>
</head>

<body>

<div class="container" id="main">
    <h1>Can you be my Valentine? 💘</h1>

    <!-- Meme image (replace link if you want) -->
    <img src="https://i.imgur.com/6b7ZQ8F.jpeg" alt="cute meme">

    <div class="buttons">
        <button id="yesBtn">YES 💖</button>
        <button id="noBtn">NO 😢</button>
    </div>
</div>

<div class="container celebration" id="celebration">
    <h1>YAAAAAY!!! 🎉💖</h1>
    <p>You just made me the happiest person alive 😍</p>
    <img src="https://i.imgur.com/1X6f8ZP.jpeg" alt="celebration meme">
</div>

<script>
    const yesBtn = document.getElementById("yesBtn");
    const noBtn = document.getElementById("noBtn");
    const main = document.getElementById("main");
    const celebration = document.getElementById("celebration");

    let yesSize = 18;

    noBtn.addEventListener("click", () => {
        yesSize += 10;
        yesBtn.style.fontSize = yesSize + "px";
        yesBtn.style.padding = (15 + yesSize/3) + "px";

        // Move NO button randomly
        const x = Math.random() * 200 - 100;
        const y = Math.random() * 100 - 50;
        noBtn.style.transform = `translate(${x}px, ${y}px)`;
    });

    yesBtn.addEventListener("click", () => {
        main.style.display = "none";
        celebration.style.display = "block";
        startHearts();
    });

    function startHearts() {
        setInterval(() => {
            const heart = document.createElement("div");
            heart.classList.add("hearts");
            heart.innerHTML = "💖";
            heart.style.left = Math.random() * 100 + "vw";
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 3000);
        }, 300);
    }
</script>

</body>
</html>
