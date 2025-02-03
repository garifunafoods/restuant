<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Garifuna Restaurant Ordering</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Welcome to Garifuna Delights</h1>
        <h2>Our Menu</h2>
        
        <div class="menu-item">
            <h3>Hudut - $12</h3>
            <p>Traditional Garifuna dish with fish and coconut milk.</p>
            <button onclick="addToOrder('Hudut', 12)">Order Now</button>
        </div>
        
        <div class="menu-item">
            <h3>Darasa - $7</h3>
            <p>Green banana tamales, a delicious and unique treat.</p>
            <button onclick="addToOrder('Darasa', 7)">Order Now</button>
        </div>
        
        <div class="menu-item">
            <h3>Tapou - $14</h3>
            <p>Garifuna seafood soup with coconut milk.</p>
            <button onclick="addToOrder('Tapou', 14)">Order Now</button>
        </div>
        
        <h2>Your Order</h2>
        <ul id="order-list"></ul>
        <h3>Total: $<span id="total-price">0</span></h3>
        <button onclick="placeOrderWhatsApp()">Order via WhatsApp</button>
    </div>
    
    <script>
        let order = [];
        let total = 0;
        
        function addToOrder(item, price) {
            order.push({ item, price });
            total += price;
            updateOrderList();
        }
        
        function updateOrderList() {
            const orderList = document.getElementById('order-list');
            orderList.innerHTML = '';
            order.forEach(orderItem => {
                const li = document.createElement('li');
                li.textContent = `${orderItem.item} - $${orderItem.price}`;
                orderList.appendChild(li);
            });
            document.getElementById('total-price').textContent = total;
        }
        
        function placeOrderWhatsApp() {
            if (order.length === 0) {
                alert('Your order is empty!');
                return;
            }
            
            let orderText = order.map(o => `${o.item} - $${o.price}`).join(", ");
            let phone = "+5016073953"; // Replace with your WhatsApp number
            let url = `https://wa.me/${phone}?text=Order%20Details:%20${encodeURIComponent(orderText)}`;
            
            window.location.href = url;
        }
    </script>
</body>
</html>
