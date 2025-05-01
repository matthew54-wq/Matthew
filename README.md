<!-- public/index.html -->
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Shop Roblox</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100">
  <div class="max-w-4xl mx-auto p-6">
    <h1 class="text-3xl font-bold text-center mb-6">Shop Bán Acc Roblox</h1>
    <div id="productList" class="grid grid-cols-1 md:grid-cols-2 gap-4"></div>
  </div>

  <script>
    fetch("/api/products")
      .then(res => res.json())
      .then(products => {
        const list = document.getElementById("productList");
        list.innerHTML = products.map(p => `
          <div class="bg-white p-4 rounded shadow">
            <h2 class="text-xl font-semibold mb-1">${p.name}</h2>
            <p>Robux: ${p.robux} | Level: ${p.level}</p>
            <p class="text-green-600 font-bold">Giá: ${p.price.toLocaleString()}đ</p>
            <form onsubmit="return submitCard(event, ${p.id})" class="mt-2 space-y-2">
              <select class="w-full p-2 border rounded" name="type">
                <option value="Viettel">Viettel</option>
                <option value="Vinaphone">Vinaphone</option>
                <option value="Mobifone">Mobifone</option>
              </select>
              <input class="w-full p-2 border rounded" name="pin" placeholder="Mã thẻ" required>
              <input class="w-full p-2 border rounded" name="serial" placeholder="Số seri" required>
              <button class="w-full bg-blue-600 text-white py-2 rounded">Mua ngay</button>
              <div class="text-sm text-red-600 result"></div>
            </form>
          </div>
        `).join("");
      });

    function submitCard(e, productId) {
      e.preventDefault();
      const form = e.target;
      const resultDiv = form.querySelector(".result");
      resultDiv.textContent = "Đang xử lý...";

      const data = {
        type: form.type.value,
        pin: form.pin.value,
        serial: form.serial.value,
        productId
      };

      fetch("/api/napthe", {
        method: "POST",
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(data)
      })
      .then(res => res.json())
      .then(res => {
        if (res.success && res.account) {
          resultDiv.innerHTML = `Thành công!<br>Username: <b>${res.account.username}</b><br>Password: <b>${res.account.password}</b>`;
        } else {
          resultDiv.textContent = res.message;
        }
      });
    }
  </script>
</body>
</html>
