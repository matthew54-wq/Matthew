<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MatthewRoblox Shop</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.1.2/dist/tailwind.min.css" rel="stylesheet">
    <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-auth.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-firestore.js"></script>
</head>
<body class="bg-gray-900 text-white">

    <header class="flex justify-between items-center p-4 bg-gray-800">
        <div class="text-2xl font-bold">MatthewRoblox Shop</div>
        <button onclick="signIn()" id="sign-in-btn" class="bg-blue-500 px-4 py-2 rounded">Sign In</button>
        <button onclick="signOut()" id="sign-out-btn" class="bg-red-500 px-4 py-2 rounded hidden">Sign Out</button>
    </header>

    <main class="container mx-auto mt-8">
        <section id="products" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
            <!-- Product cards will be inserted here dynamically -->
        </section>

        <section id="reward-section" class="mt-8 text-center">
            <button onclick="spinWheel()" class="bg-green-500 px-6 py-2 rounded">Spin the Wheel</button>
            <p id="reward-message" class="mt-4 text-lg"></p>
        </section>
    </main>

    <footer class="text-center py-6 bg-gray-800">
        <p>© 2025 MatthewRoblox Shop. All rights reserved.</p>
    </footer>

    <script src="app.js"></script>
</body>
</html>
