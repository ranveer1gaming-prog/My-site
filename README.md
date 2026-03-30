<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AnimeVault - Anime Figures & Items</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }

        .header {
            background: rgba(255,255,255,0.95);
            padding: 1rem 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 2rem;
        }

        .logo {
            font-size: 2rem;
            font-weight: bold;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .cart-info {
            display: flex;
            align-items: center;
            gap: 1rem;
            position: relative;
        }

        .cart-btn {
            background: linear-gradient(45deg, #ff6b6b, #ff8e8e);
            color: white;
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1rem;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .cart-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(255,107,107,0.4);
        }

        .cart-count {
            background: #ff4757;
            color: white;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
            font-weight: bold;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        .hero {
            text-align: center;
            color: white;
            margin-bottom: 3rem;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .hero p {
            font-size: 1.2rem;
            opacity: 0.9;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .product-card {
            background: rgba(255,255,255,0.95);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            transition: all 0.3s ease;
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }

        .product-image {
            width: 100%;
            height: 250px;
            object-fit: cover;
            transition: transform 0.3s ease;
        }

        .product-card:hover .product-image {
            transform: scale(1.05);
        }

        .product-info {
            padding: 1.5rem;
        }

        .product-title {
            font-size: 1.3rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
            color: #2c3e50;
        }

        .product-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: #e74c3c;
            margin-bottom: 1rem;
        }

        .add-to-cart {
            width: 100%;
            background: linear-gradient(45deg, #4ecdc4, #44a08d);
            color: white;
            border: none;
            padding: 0.8rem;
            border-radius: 10px;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .add-to-cart:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(78,205,196,0.4);
        }

        .cart-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 1000;
            backdrop-filter: blur(5px);
        }

        .cart-content {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            max-width: 600px;
            width: 90%;
            max-height: 80vh;
            border-radius: 20px;
            overflow-y: auto;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }

        .cart-header {
            padding: 2rem;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .close-cart {
            background: none;
            border: none;
            font-size: 2rem;
            cursor: pointer;
            color: #999;
        }

        .cart-items {
            padding: 0 2rem 2rem;
        }

        .cart-item {
            display: flex;
            gap: 1rem;
            padding: 1rem 0;
            border-bottom: 1px solid #eee;
        }

        .cart-item img {
            width: 80px;
            height: 80px;
            object-fit: cover;
            border-radius: 10px;
        }

        .cart-item-info {
            flex: 1;
        }

        .cart-item-title {
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        .cart-item-price {
            color: #e74c3c;
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        .quantity-controls {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-bottom: 1rem;
        }

        .qty-btn {
            background: #f8f9fa;
            border: 1px solid #dee2e6;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .cart-total {
            padding: 1.5rem 2rem;
            border-top: 2px solid #eee;
            background: #f8f9fa;
        }

        .total-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: #2c3e50;
            text-align: right;
        }

        .checkout-btn {
            width: 100%;
            background: linear-gradient(45deg, #ff6b6b, #ff8e8e);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 10px;
            font-size: 1.1rem;
            cursor: pointer;
            margin-top: 1rem;
            transition: all 0.3s ease;
        }

        .checkout-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(255,107,107,0.4);
        }

        .empty-cart {
            text-align: center;
            padding: 3rem;
            color: #666;
        }

        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .products-grid {
                grid-template-columns: 1fr;
                gap: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <header class="header">
        <div class="nav-container">
            <div class="logo">
                <i class="fas fa-dragon"></i> AnimeVault
            </div>
            <div class="cart-info">
                <button class="cart-btn" onclick="toggleCart()">
                    <i class="fas fa-shopping-cart"></i>
                    <span>Cart</span>
                    <div class="cart-count" id="cartCount">0</div>
                </button>
            </div>
        </div>
    </header>

    <div class="container">
        <div class="hero">
            <h1>Anime Figures Collection</h1>
            <p>Discover the ultimate collection of premium anime figures and collectibles</p>
        </div>

        <div class="products-grid" id="productsGrid">
            <!-- Products will be loaded here by JavaScript -->
        </div>
    </div>

    <!-- Cart Modal -->
    <div class="cart-modal" id="cartModal">
        <div class="cart-content">
            <div class="cart-header">
                <h2><i class="fas fa-shopping-cart"></i> Shopping Cart</h2>
                <button class="close-cart" onclick="toggleCart()">&times;</button>
            </div>
            <div class="cart-items" id="cartItems">
                <!-- Cart items will be populated here -->
            </div>
            <div class="cart-total">
                <div class="total-price" id="cartTotal">$0.00</div>
                <button class="checkout-btn" onclick="checkout()">
                    <i class="fas fa-credit-card"></i> Proceed to Checkout
                </button>
            </div>
        </div>
    </div>

    <script>
        // Product data
        const products = [
            {
                id: 1,
                title: "Goku Ultra Instinct",
                price: 89.99,
                image: "https://images.unsplash.com/photo-1572469159147-b7b7ff0fd7b2?w=400&h=300&fit=crop",
                category: "Dragon Ball"
            },
            {
                id: 2,
                title: "Luffy Gear 5",
                price: 129.99,
                image: "https://images.unsplash.com/photo-1682695796496-f2b973479a7e?w=400&h=300&fit=crop",
                category: "One Piece"
            },
            {
                id: 3,
                title: "Gojo Satoru",
                price: 99.99,
                image: "https://images.unsplash.com/photo-1672482829387-1ce74a3c4958?w=400&h=300&fit=crop",
                category: "Jujutsu Kaisen"
            },
            {
                id: 4,
                title: "Naruto Sage Mode",
                price: 79.99,
                image: "https://images.unsplash.com/photo-1578662996442-48f60103fc96?w=400&h=300&fit=crop",
                category: "Naruto"
            },
            {
                id: 5,
                title: "Demon Slayer Tanjiro",
                price: 69.99,
                image: "https://images.unsplash.com/photo-1645559150867-340cf75b7947?w=400&h=300&fit=crop",
                category: "Demon Slayer"
            },
            {
                id: 6,
                title: "Attack on Titan Levi",
                price: 109.99,
                image: "https://images.unsplash.com/photo-1628829182800-4829dac87add?w=400&h=300&fit=crop",
                category: "Attack on Titan"
            }
        ];

        // Shopping cart
        let cart = JSON.parse(localStorage.getItem('cart')) || [];

        // Initialize the page
        function init() {
            renderProducts();
            updateCartCount();
            renderCart();
        }

        // Render products
        function renderProducts() {
            const grid = document.getElementById('productsGrid');
            grid.innerHTML = products.map(product => `
                <div class="product-card">
                    <img src="${product.image}" alt="${product.title}" class="product-image">
                    <div class="product-info">
                        <div class="product-title">${product.title}</div>
                        <div class="product-price">$${product.price.toFixed(2)}</div>
                        <button class="add-to-cart" onclick="addToCart(${product.id})">
                            <i class="fas fa-cart-plus"></i> Add to Cart
                        </button>
                    </div>
                </div>
            `).join('');
        }

        // Add to cart
        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const existingItem = cart.find(item => item.id === productId);

            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({ ...product, quantity: 1 });
            }

            saveCart();
            updateCartCount();
            renderCart();
            
            // Visual feedback
            const btn = event.target.closest('.add-to-cart');
            const originalText = btn.innerHTML;
            btn.innerHTML = '<i class="fas fa-check"></i> Added!';
            btn.style.background = 'linear-gradient(45deg, #00b894, #00cec9)';
            setTimeout(() => {
                btn.innerHTML = originalText;
                btn.style.background = 'linear-gradient(45deg, #4ecdc4, #44a08d)';
            }, 1500);
        }

        // Update cart count
        function updateCartCount() {
            const count = cart.reduce((sum, item) => sum + item.quantity, 0);
            document.getElementById('cartCount').textContent = count;
        }

        // Toggle cart modal
        function toggleCart() {
            const modal = document.getElementById('cartModal');
            modal.style.display = modal.style.display === 'block' ? 'none' : 'block';
            renderCart();
        }

        // Render cart items
        function renderCart() {
            const cartItemsEl = document.getElementById('cartItems');
            const totalEl = document.getElementById('cartTotal');

            if (cart.length === 0) {
                cartItemsEl.innerHTML = `
                    <div class="empty-cart">
                        <i class="fas fa-shopping-cart" style="font-size: 4rem; color: #ddd; margin-bottom: 1rem;"></i>
                        <h3>Your cart is empty</h3>
                        <p>Add some awesome anime figures to get started!</p>
                    </div>
                `;
                totalEl.textContent = '$0.00';
                return;
            }

            cartItemsEl.innerHTML = cart.map(item => `
                <div class="cart-item">
                    <img src="${item.image}" alt="${item.title}">
                    <div class="cart-item-info">
                        <div class="cart-item-title">${item.title}</div>
                        <div class="cart-item-price">$${item.price.toFixed(2)}</div>
                        <div class="quantity-controls">
                            <button class="qty-btn" onclick="updateQuantity(${item.id}, -1)">-</button>
                            <span>${item.quantity}</span>
                            <button class="qty-btn" onclick="updateQuantity(${item.id}, 1)">+</button>
                        </div>
                        <div>$${(item.price * item.quantity).toFixed(2)}</div>
                        <button onclick="removeFromCart(${item.id})" style="background: #e74c3c; color: white; border: none; padding: 0.3rem 0.8rem; border-radius: 5px; cursor: pointer; margin-top: 0.5rem;">
                            <i class="fas fa-trash"></i> Remove
                        </button>
                    </div>
                </div>
            `).join('');

            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            totalEl.textContent = `$${total.toFixed(2)}`;
        }

        // Update quantity
        function updateQuantity(productId, change) {
            const item = cart.find(item => item.id === productId);
            if (item) {
                item.quantity += change;
                if (item.quantity <= 0) {
                    removeFromCart(productId);
                } else {
                    saveCart();
                    updateCartCount();
                    renderCart();
                }
            }
        }

        // Remove from cart
        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            saveCart();
            updateCartCount();
            renderCart();
        }

        // Save cart to localStorage
        function saveCart() {
            localStorage.setItem('cart', JSON.stringify(cart));
        }

        // Checkout
        function checkout() {
            if (cart.length === 0) return;

            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            alert(`Thank you for your purchase! Total: $${total.toFixed(2)}\n\nThis is a demo site. In a real application, you would be redirected to a payment processor.`);
            
            // Clear cart
            cart = [];
            saveCart();
            updateCartCount();
            toggleCart();
        }

        // Close cart when clicking outside
        window.onclick = function(event
