<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Be My Valentine 💘</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(135deg, #ffd6e8, #ffeef6);
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: "Comic Sans MS", cursive, sans-serif;
  overflow: hidden;
}

.container {
  text-align: center;
  background: white;
  padding: 25px 20px;
  border-radius: 20px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.1);
  width: 90%;
  max-width: 360px;
}

/* HEART IMAGE */
.heart-wrapper {
  width: 220px;
  height: 200px;
  margin: 0 auto 15px;
}

svg {
  width: 100%;
  height: 100%;
}

/* TEXT */
h1 {
  color: #ff4d88;
  margin-bottom: 20px;
}

/* BUTTONS */
.buttons {
  position: relative;
  height: 120px;
}

button {
  border: none;
  border-radius: 30px;
  padding: 12px 24px;
  font-size: 18px;
  cursor: pointer;
  transition: all 0.3s ease;
  position: absolute;
}

#yesBtn {
  background: #ff4d88;
  color: white;
  left: 50%;
  transform: translateX(-120%);
}

#noBtn {
  background: #ccc;
  color: #333;
  left: 50%;
  transform: translateX(20%);
}

/* MESSAGE */
.message {
  display: none;
  font-size: 22px;
  color: #ff4d88;
  margin-top: 20px;
}

/* FLOATING HEARTS */
.heart {
  position: fixed;
  bottom: -20px;
  font-size: 24px;
  animation: floatUp 4s linear infinite;
  opacity: 0.8;
}

@keyframes floatUp {
  0% { transform: translateY(0) scale(1); opacity: 1; }
  100% { transform: translateY(-100vh) scale(1.5); opacity: 0; }
}
</style>
</head>

<body>

<div class="container">

  <!-- PERFECT HEART SHAPE IMAGE -->
  <div class="heart-wrapper">
    <svg viewBox="0 0 32 29.6">
      <defs>
        <clipPath id="heartClip">
          <path d="M23.6,0c-3.4,0-6.4,2.1-7.6,5.1C14.8,2.1,11.8,0,8.4,0
                   C3.8,0,0,3.8,0,8.4c0,9.5,16,21.2,16,21.2
                   s16-11.7,16-21.2C32,3.8,28.2,0,23.6,0z"/>
        </clipPath>
      </defs>

      <image href="photo.jpg" width="32" height="29.6" preserveAspectRatio="xMidYMid slice" clip-path="url(#heartClip)"/>

    </svg>
  </div>

  <h1>Will you be my Valentine? 💘</h1>

  <div class="buttons">
    <button id="yesBtn">Yes 💖</button>
    <button id="noBtn">No 😢</button>
  </div>

  <div class="message" id="message">
    nhebek barcha barcha katousa rabi ikhalik laya nchalah! 💖
  </div>

</div>

<script>
const yesBtn = document.getElementById("yesBtn");
const noBtn = document.getElementById("noBtn");
const message = document.getElementById("message");

let yesSize = 1;

noBtn.addEventListener("click", () => {
  yesSize += 0.2;
  yesBtn.style.transform = `translateX(-120%) scale(${yesSize})`;

  const randomX = Math.random() * 200 - 100;
  const randomY = Math.random() * 50 - 25;

  noBtn.style.transform = `translate(${20 + randomX}px, ${randomY}px)`;
});

yesBtn.addEventListener("click", () => {
  document.querySelector(".buttons").style.display = "none";
  message.style.display = "block";
  startHearts();
});

function startHearts() {
  setInterval(() => {
    const heart = document.createElement("div");
    heart.classList.add("heart");
    heart.innerHTML = "💖";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.animationDuration = (Math.random() * 2 + 3) + "s";
    document.body.appendChild(heart);

    setTimeout(() => {
      heart.remove();
    }, 5000);
  }, 300);
}
</script>

</body>
</html>
