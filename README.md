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
        <div class="text-2xl font-bold">MatthewRoblox</div>
        <button onclick="signIn()" class="bg-blue-500 px-4 py-2 rounded">Sign In</button>
    </header>
    
    <main class="container mx-auto mt-8">
        <section id="products" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
            <!-- Products will go here -->
        </section>
    </main>
    
    <footer class="text-center py-6 bg-gray-800">
        <p>© 2025 MatthewRoblox Shop. All rights reserved.</p>
    </footer>

    <script src="app.js"></script>
</body>
</html>
// Firebase Config
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_AUTH_DOMAIN",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_STORAGE_BUCKET",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
};

// Initialize Firebase
firebase.initializeApp(firebaseConfig);
const db = firebase.firestore();
const auth = firebase.auth();

// Sign In Function
function signIn() {
    const provider = new firebase.auth.GoogleAuthProvider();
    auth.signInWithPopup(provider).then(result => {
        console.log('User signed in: ', result.user);
        // Save user data to Firestore or Firebase Realtime Database
    }).catch(error => {
        console.error(error);
    });
}

// Fetch Products from Firestore and display them
function fetchProducts() {
    db.collection('products').get().then(snapshot => {
        snapshot.forEach(doc => {
            const product = doc.data();
            const productElement = document.createElement('div');
            productElement.classList.add('bg-gray-800', 'p-4', 'rounded', 'shadow-lg');
            productElement.innerHTML = `
                <h3 class="text-xl font-semibold">${product.name}</h3>
                <p class="text-gray-400">${product.description}</p>
                <button onclick="buyProduct('${product.id}')" class="bg-blue-500 px-4 py-2 rounded mt-4">Buy Now</button>
            `;
            document.getElementById('products').appendChild(productElement);
        });
    });
}

// Buy Product Function
function buyProduct(productId) {
    const user = auth.currentUser;
    if (!user) {
        alert('Please sign in to buy products.');
        return;
    }

    // Handle product purchase logic here (update Firestore, etc.)
    db.collection('purchases').add({
        userId: user.uid,
        productId: productId,
        timestamp: firebase.firestore.FieldValue.serverTimestamp()
    }).then(() => {
        alert('Product purchased successfully!');
    }).catch(error => {
        console.error(error);
    });
}

// Initialize page
window.onload = () => {
    fetchProducts();
};
/* Add custom styles here if needed */
