<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>MatthewRoblox.com - Shop Roblox Uy Tín</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; background: #111; color: #fff; }
    header { background: #4CAF50; padding: 30px; text-align: center; }
    header h1 { margin: 0; font-size: 36px; }
    nav { background: #222; padding: 10px; text-align: center; }
    nav a { color: white; margin: 0 15px; text-decoration: none; font-weight: bold; }
    .section { padding: 20px; }
    .product { background: #222; padding: 15px; margin: 10px auto; border-radius: 10px; max-width: 500px; text-align: center; }
    .product img { max-width: 100%; border-radius: 10px; }
    .product .buy { display: inline-block; margin-top: 10px; padding: 10px 20px; background: #4CAF50; color: #fff; border-radius: 5px; text-decoration: none; }
    .wheel-container { text-align: center; margin-top: 40px; }
    .spin-button { margin-top: 15px; padding: 12px 20px; background: #4CAF50; color: white; border: none; border-radius: 5px; font-size: 16px; cursor: pointer; }
    canvas { background: #222; border-radius: 50%; margin-top: 20px; }
  </style>
</head>
<body>

<header>
  <h1>MatthewRoblox.com</h1>
  <p>Shop Acc, Gamepass, Robux và Vòng Quay Trúng Thưởng</p>
</header>

<nav>
  <a href="#products">Sản phẩm</a>
  <a href="#spin">Vòng quay</a>
  <a href="#contact">Liên hệ</a>
</nav>

<div class="section" id="products">
  <h2>Sản phẩm nổi bật</h2>
  <div class="product">
    <img src="https://via.placeholder.com/400x200.png?text=Acc+SSS" alt="Acc SSS">
    <h3>Acc Roblox SSS Siêu Hiếm</h3>
    <p>Giá: 250K VNĐ</p>
    <a class="buy" href="https://zalo.me">Mua ngay qua Zalo</a>
  </div>
  <div class="product">
    <img src="https://via.placeholder.com/400x200.png?text=Gamepass+x2+EXP" alt="Gamepass">
    <h3>Gamepass x2 EXP Blox Fruits</h3>
    <p>Giá: 80K VNĐ</p>
    <a class="buy" href="https://facebook.com">Mua ngay qua Facebook</a>
  </div>
</div>

<div class="section" id="spin">
  <h2>🎰 Vòng Quay Trúng Thưởng – 10K / lượt</h2>
  <div class="wheel-container">
    <canvas id="wheel" width="300" height="300"></canvas><br>
    <button class="spin-button" onclick="spinWheel()">Quay Ngay</button>
    <p><small>Liên hệ Zalo để thanh toán và nhận phần thưởng.</small></p>
  </div>
</div>

<div class="section" id="contact">
  <h2>Liên hệ</h2>
  <p>Zalo: <a href="https://zalo.me" style="color:#4CAF50">https://zalo.me</a></p>
  <p>Facebook: <a href="https://facebook.com" style="color:#4CAF50">https://facebook.com</a></p>
</div>

<script>
const canvas = document.getElementById('wheel');
const ctx = canvas.getContext('2d');
const rewards = ["Acc SSS", "200 Robux", "Gamepass", "Acc VIP", "Acc SSR", "Quay lại", "Không trúng", "500 Robux"];
const colors = ["#4CAF50", "#2E7D32", "#66BB6A", "#81C784", "#A5D6A7", "#388E3C", "#C8E6C9", "#1B5E20"];
const size = rewards.length;
const arc = Math.PI * 2 / size;
let angle = 0;

function drawWheel() {
  for (let i = 0; i < size; i++) {
    const start = angle + i * arc;
    ctx.beginPath();
    ctx.fillStyle = colors[i % colors.length];
    ctx.moveTo(150, 150);
    ctx.arc(150, 150, 150, start, start + arc);
    ctx.lineTo(150, 150);
    ctx.fill();
    ctx.fillStyle = "#000";
    ctx.font = "14px Arial";
    ctx.save();
    ctx.translate(150, 150);
    ctx.rotate(start + arc / 2);
    ctx.fillText(rewards[i], 60, 5);
    ctx.restore();
  }
}

function spinWheel() {
  const spinAngle = Math.random() * 360 + 720;
  canvas.style.transition = "transform 4s ease-out";
  canvas.style.transform = `rotate(${spinAngle}deg)`;
  setTimeout(() => alert("🎁 Cảm ơn bạn! Hãy liên hệ Zalo để nhận phần thưởng."), 4200);
}

drawWheel();
</script>

</body>
</html>
