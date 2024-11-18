<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">   <meta name="description" content="SpareXpress - надежные запчасти для вашего авто с акциями и быстрой доставкой.">
  <meta name="keywords" content="автозапчасти, запчасти для авто, SpareXpress, автоаксессуары">
  <meta name="author" content="SpareXpress">
  <title>SpareXpress</title>
  <style>
    /* Основные стили */
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #000;
      color: white;
    }
    header {
      background-color: #000;
      padding: 20px;
      position: sticky;
      top: 0;
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-bottom: 2px solid white;
    }
    .logo {
      font-size: 24px;
      text-transform: uppercase;
      font-weight: bold;
    }
    .menu-icon {
      cursor: pointer;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      height: 24px;
      width: 30px;
    }
    .menu-icon div {
      background-color: white;
      height: 4px;
      width: 100%;
      border-radius: 2px;
    }
    .search-bar {
      flex-grow: 1;
      margin: 0 20px;
    }
    .search-bar input {
      padding: 10px;
      width: 100%;
      max-width: 600px;
      border: none;
      border-radius: 5px;
      font-size: 16px;
    }
    /* Горизонтальная лента рекламы */
    .ad-banner {
      display: flex;
      overflow-x: auto;
      white-space: nowrap;
      background-color: #111;
      padding: 10px;
      border-bottom: 2px solid white;
    }
    .ad-banner div {
      flex: 0 0 auto;
      background-color: #222;
      border-radius: 5px;
      padding: 10px 20px;
      margin-right: 10px;
      font-size: 16px;
      text-align: center;
      color: #fff;
    }
    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 10px;
      padding: 20px;
    }
    .product-card {
      background: #111;
      border-radius: 10px;
      padding: 10px;
      text-align: center;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }
    .product-card:hover {
      transform: scale(1.05);
      box-shadow: 0 6px 8px rgba(255, 255, 255, 0.2);
    }
    .product-card img {
      width: 100%;
      height: auto;
      border-radius: 10px;
    }
    .btn {
      background-color: #007bff;
      color: white;
      padding: 10px 15px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 10px;
      transition: background-color 0.3s ease;
    }
    .btn:hover {
      background-color: #0056b3;
    }
    footer {
      background-color: #0b0b0b;
      text-align: center;
      padding: 10px;
      color: white;
    }
    #menu {
      position: fixed;
      top: 60px;
      right: 0;
      background-color: #111;
      width: 250px;
      height: 100vh;
      box-shadow: -2px 0 5px rgba(255, 255, 255, 0.2);
      transform: translateX(100%);
      transition: transform 0.3s ease;
      z-index: 1000;
      padding: 20px;
      color: white;
    }
    #menu.open {
      transform: translateX(0);
    }
    #menu ul {
      list-style: none;
      padding: 0;
    }
    #menu ul li {
      margin: 15px 0;
      font-size: 18px;
    }
    #menu ul li a {
      text-decoration: none;
      color: white;
      transition: color 0.3s ease;
    }
    #menu ul li a:hover {
      color: #007bff;
    }
    @media (max-width: 768px) {
      header {
        flex-wrap: wrap;
        text-align: center;
      }
    }
  </style>
</head>
<body>
  <header>
    <div class="logo">sparexpress</div>
    <div class="search-bar">
      <input type="text" placeholder="Поиск запчастей...">
    </div>
    <div class="menu-icon" onclick="toggleMenu()">
      <div></div>
      <div></div>
      <div></div>
    </div>
  </header>
  
  <!-- Горизонтальная лента рекламы -->
  <div class="ad-banner">
    <div>Скидка 20% на тормозные колодки!</div>
    <div>Купи фильтр - получи масло в подарок!</div>
    <div>Бесплатная доставка при заказе от 10 000 тг.</div>
    <div>Эксклюзивные запчасти по лучшим ценам!</div>
  </div>

  <div id="menu">
    <ul>
      <li><strong>Контакты:</strong></li>
      <li>Телефон: +7 777 123-45-67</li>
      <li>Email: support@sparexpress.kz</li>
      <li><strong>Адрес:</strong></li>
      <li>г. Алматы, ул. Абая, д. 25</li>
    </ul>
  </div>

  <!-- Продукты -->
  <div class="products" id="product-container"></div>

  <footer>
    &copy; 2024 SpareXpress. Все права защищены.
  </footer>

  <script>
    const products = [
      { name: "Тормозные колодки", image: "https://avatars.mds.yandex.net/i?id=2f6d96e74bd31fc89b7676981c55158f_l-4936060-images-thumbs&n=13" },
      { name: "Фильтр воздушный", image: "https://kshm.ru/wa-data/public/shop/products/76/59/5976/images/340/340.750x0.jpeg" },
      { name: "Масляный насос", image: "https://avatars.mds.yandex.net/i?id=96d08493be294ed1eaa5b821ba83263a_l-5869767-images-thumbs&n=13" },
      { name: "Свечи зажигания", image: "https://avatars.mds.yandex.net/i?id=b7bd5a97bfc3d36a5eff2096ecfa197a_l-5086971-images-thumbs&n=13" },
      { name: "Ремень ГРМ", image: "https://akbsibir.ru/images/product_images/popup_images/199_1.jpg" },
    ];

    const container = document.getElementById("product-container");

    products.forEach((product) => {
      const card = document.createElement("div");
      card.className = "product-card";
      
      card.innerHTML = `
        <h3>${product.name}</h3>
        <img src="${product.image}" alt="${product.name}">
        <button class="btn" onclick="alert('Добавлено в корзину!')">Купить</button>
      `;
      
      container.appendChild(card);
    });

    function toggleMenu() {
      const menu = document.getElementById('menu');
      menu.classList.toggle('open');
    }
  </script>
</body>
</html>
