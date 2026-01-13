 WhoFingKnew's Digital Boutique

Welcome to My Digital Boutique, a cozy little online shop where creativity meets convenience. Here, you can browse, collect, and download digital treasures like eBooks, designs, art, and more—all crafted to inspire and delight
🧡 Creator-Owned  

index.html
style.css
script.js
products.json


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>My Digital Boutique</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="style.css">
</head>
<body>

<header>
  <h1>🌸 My Digital Boutique</h1>
  <p class="tagline">A small shop for lovely digital things</p>
  <div class="cart">
    🧺 Cart Total: $<span id="total">0</span>
    <button id="checkoutBtn">Checkout</button>
  </div>
</header>

<main id="products"></main>

<footer>
  <p>Made with care & curiosity ✨</p>
</footer>

<script src="script.js"></script>
</body>
</html>


body {
  font-family: system-ui, sans-serif;
  margin: 0;
  background: #fffaf7;
  color: #333;
}

header {
  text-align: center;
  padding: 2rem;
  background: #ffe4ec;
}

.tagline {
  font-style: italic;
  margin-top: 0.5rem;
}

.cart {
  margin-top: 1rem;
}

button {
  background: #ff7aa2;
  border: none;
  padding: 0.5rem 1rem;
  color: white;
  cursor: pointer;
  border-radius: 5px;
}

button:hover {
  background: #ff5f8a;
}

#products {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.5rem;
  padding: 2rem;
}

.product {
  background: white;
  border-radius: 10px;
  padding: 1rem;
  box-shadow: 0 4px 10px rgba(0,0,0,0.05);
  text-align: center;
}

.product img {
  width: 100%;
  border-radius: 8px;
}

footer {
  text-align: center;
  padding: 2rem;
  font-size: 0.9rem;
  color: #777;
}


[
  {
    "id": 1,
    "name": "Romantic Poetry eBook",
    "price": 10,
    "file": "downloads/romantic-poetry.pdf",
    "image": "https://via.placeholder.com/300x200?text=Poetry+Book"
  },
  {
    "id": 2,
    "name": "Printable Art Set",
    "price": 6,
    "file": "downloads/printable-art.zip",
    "image": "https://via.placeholder.com/300x200?text=Printable+Art"
  }
]


let cart = [];
let total = 0;

fetch('products.json')
  .then(res => res.json())
  .then(products => {
    const container = document.getElementById('products');

    products.forEach(product => {
      const card = document.createElement('div');
      card.className = 'product';

      card.innerHTML = `
        <img src="${product.image}" alt="${product.name}">
        <h3>${product.name}</h3>
        <p>$${product.price}</p>
        <button onclick="addToCart(${product.id})">Add to Cart</button>
      `;

      container.appendChild(card);
    });

    window.allProducts = products;
  });

function addToCart(id) {
  const product = window.allProducts.find(p => p.id === id);
  cart.push(product);
  total += product.price;
  document.getElementById('total').textContent = total;
}

document.getElementById('checkoutBtn').addEventListener('click', () => {
  if (cart.length === 0) {
    alert("Your basket is empty 🌱");
    return;
  }

  let message = "Thank you for visiting the shop 💖\n\nYour downloads:\n\n";

  cart.forEach(item => {
    message += `${item.name}\n${item.file}\n\n`;
  });

  alert(message);

  cart = [];
  total = 0;
  document.getElementById('total').textContent = total;
});

<footer>
  <p>Made with care by WhoFingKnew ✨</p>
</footer>

https://whofingknew.github.io/my-digital-boutique
