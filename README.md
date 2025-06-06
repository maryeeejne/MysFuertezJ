<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mys J Threads</title>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Roboto:wght@400;500&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif; /* Default font for body */
            background-color: #e0f7fa;
            margin: 0;
            padding: 0;
            color: #333;
        }

        header {
            position: relative;
            background-image: url('me.jpg'); /* Replace 'your-image-url.jpg' with your image file */
            background-size: cover; /* Ensure the background covers the entire header */
            background-position: center;
            color: white;
            padding: 30px 20px;
            text-align: center;
            font-family: 'Pacifico', cursive; /* Use Pacifico font for business name */
            font-size: 3rem; /* Larger font size for business name */
            letter-spacing: 2px;
            animation: fadeIn 1.5s ease-out;
        }

        header::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.4); /* Semi-transparent black overlay */
            z-index: 1; /* Put the overlay above the background but below the text */
        }

        header span {
            font-family: 'Roboto', sans-serif; /* Use Roboto font for tagline */
            font-size: 1.2rem;
            font-weight: 400;
            display: block; /* To make the tagline appear below the business name */
            margin-top: 10px;
            z-index: 2; /* Ensure text stays on top of the overlay */
            position: relative; /* Position it above the overlay */
        }

        nav {
            background-color: #008CBA;
            padding: 15px 0;
            display: flex;
            justify-content: center;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        }

        nav a {
            color: white;
            padding: 14px 25px;
            text-decoration: none;
            text-align: center;
            margin: 0 20px;
            font-size: 1.1rem;
            font-weight: 500;
            border-radius: 5px;
            transition: background-color 0.3s ease, transform 0.3s ease;
        }

        nav a:hover {
            background-color: #005f73;
            transform: scale(1.05);
        }

        .product-section {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            padding: 40px;
            animation: fadeIn 2s ease-out;
        }

        .product-card {
            background-color: #ffffff;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            padding: 20px;
            text-align: center;
            margin: 20px;
            width: 250px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .product-card:hover {
            transform: scale(1.05);
            box-shadow: 0 6px 10px rgba(0, 0, 0, 0.2);
        }

        .product-image {
            width: 100%;
            height: 150px;
            object-fit: cover;
            border-radius: 8px;
            transition: opacity 0.3s ease;
        }

        .product-name {
            font-size: 1.2rem;
            margin-top: 10px;
            font-weight: bold;
        }

        .product-price {
            color: #00796b;
            margin: 10px 0;
            font-size: 1.1rem;
        }

        .add-to-cart-btn {
            background-color: #004d40;
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.3s ease;
        }

        .add-to-cart-btn:hover {
            background-color: #00796b;
            transform: scale(1.05);
        }

        .cart {
            padding: 20px;
            background-color: #ffffff;
            margin: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            display: none;
            position: fixed;
            top: 0;
            right: 0;
            width: 300px;
            height: 100%;
            overflow-y: auto;
            z-index: 1000;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
        }

        .cart h2 {
            font-size: 1.5rem;
            margin-bottom: 20px;
        }

        .cart-item {
            padding: 10px;
            border-bottom: 1px solid #ccc;
            font-size: 1rem;
        }

        .checkout-btn {
            background-color: #0066cc;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            display: block;
            width: 100%;
            font-size: 1.2rem;
            margin-top: 20px;
            transition: background-color 0.3s ease;
        }

        .checkout-btn:hover {
            background-color: #004d99;
        }

        footer {
            background-color: #0066cc;
            color: white;
            text-align: center;
            padding: 20px;
            margin-top: 40px;
            font-size: 1rem;
        }

        @keyframes fadeIn {
            0% { opacity: 0; }
            100% { opacity: 1; }
        }

    </style>
</head>
<body>
    <header>
        Mys J Threads
        <span>"Where yarn and heart collide"</span>
    </header>
    
    <nav>
        <a href="#home">Home</a>
        <a href="#products">Products</a>
        <a href="#cart" onclick="toggleCart()">Cart</a>
        <a href="#create-account">Create Account</a>
    </nav>

    <section class="product-section" id="products">
        <div class="product-card">
            <img src="twirlytentacle.jpg" alt="Twirly Tentacle" class="product-image">
            <div class="product-name">Twirly Tentacle</div>
            <div class="product-price">PHP 25.00</div>
            <button class="add-to-cart-btn" onclick="addToCart('Twirly Tentacle', 25.00)">Add to Cart</button>
        </div>

        <div class="product-card">
            <img src="star.jpg" alt="Star" class="product-image">
            <div class="product-name">Star</div>
            <div class="product-price">PHP 25.00</div>
            <button class="add-to-cart-btn" onclick="addToCart('Star', 25.00)">Add to Cart</button>
        </div>

        <div class="product-card">
            <img src="heart.jpg" alt="Heart" class="product-image">
            <div class="product-name">Heart</div>
            <div class="product-price">PHP 30.00</div>
            <button class="add-to-cart-btn" onclick="addToCart('Heart', 30.00)">Add to Cart</button>
        </div>

        <div class="product-card">
            <img src="cakeroll.jpg" alt="Cake Roll" class="product-image">
            <div class="product-name">Cake Roll</div>
            <div class="product-price">PHP 30.00</div>
            <button class="add-to-cart-btn" onclick="addToCart('Cake Roll', 30.00)">Add to Cart</button>
        </div>
    </section>

    <section id="cart" class="cart">
        <h2>Your Cart</h2>
        <div id="cart-items"></div>
        <button class="checkout-btn" onclick="checkout()">Checkout</button>
    </section>

    <footer>
        FUERTEZ MARY JANE T.<br>
        12 STEM- CELSIUS<br>
        EMPOWERMENT TECHNOLOGIES
    </footer>

    <script>
        let cart = [];

        function addToCart(productName, price) {
            cart.push({ productName, price });
            updateCart();
        }

        function updateCart() {
            let cartItems = document.getElementById('cart-items');
            cartItems.innerHTML = '';
            if (cart.length === 0) {
                cartItems.innerHTML = "<p>Your cart is empty.</p>";
            } else {
                cart.forEach(item => {
                    let div = document.createElement('div');
                    div.className = 'cart-item';
                    div.innerText = `${item.productName} - PHP ${item.price}`;
                    cartItems.appendChild(div);
                });
            }
            document.querySelector('.cart').style.display = 'block';
        }

        function toggleCart() {
            const cartSection = document.querySelector('.cart');
            cartSection.style.display = cartSection.style.display === 'block' ? 'none' : 'block';
        }

        function checkout() {
            if (cart.length === 0) {
                alert("Your cart is empty. Please add items to your cart before proceeding.");
            } else {
                alert('Proceeding to checkout...');
            }
        }
    </script>
</body>
</html>
