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
<div class="section" id="leaderboard">
  <h2>🏆 Bảng Xếp Hạng Ủng Hộ</h2>
  <table style="width: 100%; max-width: 600px; margin: auto; background: #222; border-collapse: collapse;">
    <thead>
      <tr style="background: #4CAF50;">
        <th style="padding: 10px;">Hạng</th>
        <th style="padding: 10px;">Tên</th>
        <th style="padding: 10px;">Số tiền ủng hộ</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="text-align: center;">🥇 1</td>
        <td style="text-align: center;">Nguyễn Văn A</td>
        <td style="text-align: center;">500K</td>
      </tr>
      <tr>
        <td style="text-align: center;">🥈 2</td>
        <td style="text-align: center;">Lê B</td>
        <td style="text-align: center;">300K</td>
      </tr>
      <tr>
        <td style="text-align: center;">🥉 3</td>
        <td style="text-align: center;">Trần C</td>
        <td style="text-align: center;">200K</td>
      </tr>
    </tbody>
  </table>
</div>
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MatthewRoblox.com - Shop Roblox</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; background: #111; color: #fff; }
    header { background: #4CAF50; padding: 30px; text-align: center; }
    nav { background: #222; padding: 10px; text-align: center; }
    nav a { color: white; margin: 0 15px; text-decoration: none; font-weight: bold; }
    .section { padding: 20px; }
    .product, .acc-item { background: #222; padding: 15px; margin: 10px auto; border-radius: 10px; max-width: 600px; text-align: center; }
    .product img, .acc-item img { max-width: 100%; border-radius: 10px; }
    .buy, .support-btn { display: inline-block; margin-top: 10px; padding: 10px 20px; background: #4CAF50; color: #fff; border-radius: 5px; text-decoration: none; }
    .input-box { padding: 10px; margin: 5px 0; width: 80%; max-width: 400px; }
    .acc-list { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; }
    .support-box { background: #222; padding: 20px; border-radius: 10px; max-width: 600px; margin: auto; }
    table { width: 100%; border-collapse: collapse; margin-top: 20px; }
    th, td { padding: 10px; text-align: center; }
    th { background: #4CAF50; }
    tr:nth-child(even) { background: #333; }
    @media (min-width: 768px) {
      header h1 { font-size: 48px; }
      nav a { margin: 0 25px; font-size: 18px; }
    }
  </style>
</head>
<body>

<header>
  <h1>MatthewRoblox.com</h1>
  <p>Shop Acc, Robux & Vòng Quay Tự Động</p>
</header>

<nav>
  <a href="#top">Trang chủ</a>
  <a href="#recharge">Nạp tiền</a>
  <a href="#accshop">Mua acc</a>
  <a href="#spin">Vòng quay</a>
  <a href="#leaderboard">BXH</a>
  <a href="#support">CSKH</a>
</nav>

<div class="section" id="recharge">
  <h2>💰 Nạp tiền vào tài khoản</h2>
  <p>Chọn phương thức và quét mã để nạp:</p>
  <input class="input-box" type="text" placeholder="Nhập tên Roblox hoặc ID">
  <br>
  <img src="https://via.placeholder.com/250x250.png?text=Momo+QR" alt="QR Momo">
  <p>Nội dung chuyển khoản: <strong>NAP [Tên bạn]</strong></p>
</div>

<div class="section" id="accshop">
  <h2>🛒 Mua Acc Tự Động</h2>
  <div class="acc-list">
    <div class="acc-item">
      <img src="https://via.placeholder.com/400x200.png?text=Acc+VIP">
      <h3>Acc VIP - Lv 999</h3>
      <p>Giá: 150K</p>
      <button class="buy">Mua ngay</button>
    </div>
    <div class="acc-item">
      <img src="https://via.placeholder.com/400x200.png?text=Acc+SSS">
      <h3>Acc SSS - Full Gamepass</h3>
      <p>Giá: 300K</p>
      <button class="buy">Mua ngay</button>
    </div>
  </div>
</div>

<div class="section" id="spin">
  <h2>🎰 Vòng Quay May Mắn – 10K/Lượt</h2>
  <canvas id="wheel" width="300" height="300" style="display: block; margin: auto;"></canvas>
  <button class="buy" onclick="spinWheel()">Quay ngay</button>
</div>

<div class="section" id="leaderboard">
  <h2>🏆 Bảng Xếp Hạng Ủng Hộ</h2>
  <table>
    <tr><th>Hạng</th><th>Tên</th><th>Số tiền</th></tr>
    <tr><td>1</td><td>Nguyễn Văn A</td><td>500K</td></tr>
    <tr><td>2</td><td>Lê B</td><td>300K</td></tr>
    <tr><td>3</td><td>Trần C</td><td>200K</td></tr>
  </table>
</div>

<div class="section" id="support">
  <h2>📞 Hỗ Trợ & CSKH</h2>
  <div class="support-box">
    <p>Zalo: <a href="https://zalo.me" class="support-btn">Liên hệ Zalo</a></p>
    <p>Facebook: <a href="https://facebook.com" class="support-btn">Inbox Facebook</a></p>
    <p>Email: support@matthewroblox.com</p>
  </div>
</div>

<script>
const canvas = document.getElementById('wheel');
const ctx = canvas.getContext('2d');
const rewards = ["Acc SSS", "200 Robux", "Gamepass", "Acc VIP", "500 Robux", "Quay lại", "Không trúng", "100 Robux"];
const arc = Math.PI * 2 / rewards.length;
function drawWheel() {
  for (let i = 0; i < rewards.length; i++) {
    const angle = i * arc;
    ctx.beginPath();
    ctx.fillStyle = i % 2 ? '#66BB6A' : '#4CAF50';
    ctx.moveTo(150, 150);
    ctx.arc(150, 150, 150, angle, angle + arc);
    ctx.lineTo(150, 150);
    ctx.fill();
    ctx.save();
    ctx.translate(150, 150);
    ctx.rotate(angle + arc / 2);
    ctx.fillStyle = '#000';
    ctx.fillText(rewards[i], 60, 5);
    ctx.restore();
  }
}
drawWheel();
function spinWheel() {
  const deg = Math.floor(Math.random() * 360 + 720);
  canvas.style.transition = 'transform 4s ease-out';
  canvas.style.transform = `rotate(${deg}deg)`;
  setTimeout(() => alert("🎉 Cảm ơn! Liên hệ Zalo để nhận phần thưởng!"), 4200);
}
</script>

</body>
</html>
