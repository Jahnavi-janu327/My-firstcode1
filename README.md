<!DOCTYPE html>
<html>
<head>
    <title>Pizza Delivery</title>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
    <header>
        <h1>Welcome to Pizza Delivery</h1>
    </header>

    <div class="menu">
        <h2>Menu</h2>
        <ul>
            <li>
                <h3>Pizza Margherita</h3>
                <p>Tomato sauce, mozzarella cheese, basil</p>
                <button onclick="addToCart('Pizza Margherita')">Add to Cart</button>
            </li>
            <li>
                <h3>Pepperoni Pizza</h3>
                <p>Tomato sauce, mozzarella cheese, pepperoni</p>
                <button onclick="addToCart('Pepperoni Pizza')">Add to Cart</button>
            </li>
        </ul>
    </div>

    <div class="cart">
        <h2>Cart</h2>
        <ul id="cart-items">
            <!-- Cart items will be displayed here -->
        </ul>
        <p>Total: <span id="cart-total">$0.00</span></p>
        <button onclick="placeOrder()">Place Order</button>
    </div>

    <script>
        let cart = [];
        let total = 0;

        function addToCart(item) {
            cart.push(item);
            total += 10; // Assuming a fixed price per pizza
            updateCartUI();
        }

        function updateCartUI() {
            const cartItems = document.getElementById('cart-items');
            const cartTotal = document.getElementById('cart-total');
            cartItems.innerHTML = '';
            cart.forEach(item => {
                const li = document.createElement('li');
                li.textContent = item;
                cartItems.appendChild(li);
            });
            cartTotal.textContent = `$${total.toFixed(2)}`;
        }

        function placeOrder() {
            if (cart.length === 0) {
                alert('Your cart is empty. Please add items before placing an order.');
            } else {
                alert(`Order placed with a total of $${total.toFixed(2)}. Thank you!`);
                cart = [];
                total = 0;
                updateCartUI();
            }
        }
    </script>
</body>
</html>
