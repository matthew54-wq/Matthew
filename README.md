<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Shop Roblox</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 text-gray-800">
  <header class="bg-black text-white p-4">
    <div class="container mx-auto flex justify-between items-center">
      <h1 class="text-2xl font-bold">Shop Roblox</h1>
      <a href="/admin" class="text-sm hover:underline">Đăng nhập Admin</a>
    </div>
  </header>

  <main class="container mx-auto p-4">
    <h2 class="text-xl font-semibold mb-4">Danh sách tài khoản Roblox</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <!-- Tài khoản 1 -->
      <div class="bg-white p-4 rounded shadow">
        <img src="https://tr.rbxcdn.com/64x64-avatar.png" alt="avatar" class="w-16 h-16 rounded-full mx-auto mb-2">
        <h3 class="text-lg font-bold text-center">Acc #1</h3>
        <p class="text-center">Robux: 120 | Level: 25</p>
        <p class="text-center text-green-600 font-semibold">Giá: 50.000đ</p>
        <a href="product.html?id=1" class="block mt-4 bg-blue-600 text-white text-center py-2 rounded hover:bg-blue-700">Mua ngay</a>
      </div>
      <!-- Thêm nhiều acc khác tương tự -->
    </div>
  </main>

  <footer class="bg-black text-white text-center p-4 mt-8">
    &copy; 2025 ShopRoblox.com | Liên hệ: 090xxxxxx
  </footer>
</body>
</html>
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Mua Acc Roblox</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 p-4">
  <div class="max-w-xl mx-auto bg-white p-6 rounded shadow">
    <h1 class="text-2xl font-bold mb-4">Mua Acc Roblox #1</h1>
    <img src="https://tr.rbxcdn.com/64x64-avatar.png" class="w-24 h-24 mx-auto rounded mb-2" />
    <p class="text-center">Robux: 120 | Level: 25</p>
    <p class="text-center text-green-600 text-lg font-bold mb-4">Giá: 50.000đ</p>

    <form id="cardForm" class="space-y-3">
      <div>
        <label class="block">Loại thẻ</label>
        <select id="cardType" class="w-full border p-2 rounded">
          <option value="Viettel">Viettel</option>
          <option value="Vinaphone">Vinaphone</option>
          <option value="Mobifone">Mobifone</option>
        </select>
      </div>
      <div>
        <label class="block">Mã thẻ</label>
        <input type="text" id="pin" class="w-full border p-2 rounded" required>
      </div>
      <div>
        <label class="block">Số seri</label>
        <input type="text" id="serial" class="w-full border p-2 rounded" required>
      </div>
      <button type="submit" class="w-full bg-blue-600 text-white py-2 rounded hover:bg-blue-700">
        Gửi thanh toán
      </button>
    </form>

    <div id="result" class="mt-4 text-center font-semibold"></div>
  </div>

  <script>
    document.getElementById("cardForm").addEventListener("submit", async (e) => {
      e.preventDefault();
      const type = document.getElementById("cardType").value;
      const pin = document.getElementById("pin").value;
      const serial = document.getElementById("serial").value;

      document.getElementById("result").innerText = "Đang xử lý...";

      // Gửi dữ liệu tới server (giả lập)
      const res = await fetch("/api/napthe", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ type, pin, serial })
      });

      const data = await res.json();
      document.getElementById("result").innerText = data.message;
    });
  </script>
</body>
</html>
// server/app.js
const express = require("express");
const bodyParser = require("body-parser");
const cors = require("cors");
const app = express();
const PORT = 3000;

let orders = []; // Giả lập lưu đơn hàng
let products = [
  {
    id: 1,
    name: "Acc Roblox #1",
    robux: 120,
    level: 25,
    price: 50000,
    delivered: false,
    username: "roblox_user_001",
    password: "abc123xyz"
  },
  // Thêm nhiều acc khác nếu muốn
];

app.use(cors());
app.use(bodyParser.json());
app.use(express.static("public"));

// API lấy danh sách sản phẩm
app.get("/api/products", (req, res) => {
  res.json(products);
});

// API xử lý nạp thẻ và giao acc (giả lập)
app.post("/api/napthe", async (req, res) => {
  const { type, pin, serial, productId } = req.body;

  if (pin.length >= 10 && serial.length >= 10) {
    const product = products.find(p => p.id == productId);
    if (!product || product.delivered) {
      return res.json({ success: false, message: "Sản phẩm không tồn tại hoặc đã bán." });
    }

    // Lưu đơn hàng
    const order = {
      id: orders.length + 1,
      productId: product.id,
      telco: type,
      pin,
      serial,
      date: new Date(),
      delivered: true
    };
    orders.push(order);
    product.delivered = true;

    return res.json({
      success: true,
      message: "Nạp thẻ thành công! Đây là tài khoản của bạn:",
      account: {
        username: product.username,
        password: product.password
      }
    });
  } else {
    return res.json({ success: false, message: "Mã thẻ hoặc seri không hợp lệ." });
  }
});

// API admin: danh sách đơn hàng
app.get("/api/admin/orders", (req, res) => {
  res.json(orders);
});

// API admin: danh sách acc
app.get("/api/admin/products", (req, res) => {
  res.json(products);
});

app.listen(PORT, () => {
  console.log(`Server đang chạy tại http://localhost:${PORT}`);
});

