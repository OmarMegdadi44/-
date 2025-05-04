<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ريشة - متجر الملابس</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <header>
    <div class="container">
      <h1 class="logo">🧥 ريشة</h1>
      <nav>
        <ul>
          <li><a href="index.html">الرئيسية</a></li>
          <li><a href="products.html">المنتجات</a></li>
          <li><a href="cart.html">السلة</a></li>
          <li><a href="login.html">تسجيل الدخول</a></li>
        </ul>
      </nav>
    </div>
  </header>

  <section class="hero">
    <div class="container">
      <h2>اكتشف أزياء رائعة</h2>
      <p>أفضل الملابس بأفضل الأسعار</p>
      <a href="products.html" class="btn">تسوق الآن</a>
    </div>
  </section>

  <footer>
    <div class="container">
      <p>© 2025 جميع الحقوق محفوظة - ريشة</p>
    </div>
  </footer>
</body>
</html>
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>المنتجات - ريشة</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <header>
    <div class="container">
      <h1 class="logo">🧥 ريشة</h1>
      <nav>
        <ul>
          <li><a href="index.html">الرئيسية</a></li>
          <li><a href="products.html">المنتجات</a></li>
          <li><a href="cart.html">السلة</a></li>
          <li><a href="login.html">تسجيل الدخول</a></li>
        </ul>
      </nav>
    </div>
  </header>

  <section class="product-list">
    <div class="container">
      <h2>المنتجات المتوفرة</h2>
      <div class="product">
        <img src="shirt.jpg" alt="قميص" />
        <h3>قميص رجالي</h3>
        <p>15 د.أ</p>
        <button class="add-to-cart-btn" data-name="قميص رجالي" data-price="15">أضف إلى السلة</button>
      </div>

      <div class="product">
        <img src="dress.jpg" alt="فستان" />
        <h3>فستان نسائي</h3>
        <p>20 د.أ</p>
        <button class="add-to-cart-btn" data-name="فستان نسائي" data-price="20">أضف إلى السلة</button>
      </div>
    </div>
  </section>

  <footer>
    <div class="container">
      <p>© 2025 جميع الحقوق محفوظة - ريشة</p>
    </div>
  </footer>

  <script>
    function addToCart(productName, productPrice) {
      const product = { name: productName, price: productPrice };
      let cart = JSON.parse(localStorage.getItem('cart')) || [];
      cart.push(product);
      localStorage.setItem('cart', JSON.stringify(cart));
      alert(`${productName} تم إضافته إلى السلة`);
    }

    document.querySelectorAll('.add-to-cart-btn').forEach(button => {
      button.addEventListener('click', (e) => {
        const productName = e.target.getAttribute('data-name');
        const productPrice = parseFloat(e.target.getAttribute('data-price'));
        addToCart(productName, productPrice);
      });
    });
  </script>

</body>
</html>
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>سلة الشراء - ريشة</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <header>
    <div class="container">
      <h1 class="logo">🧥 ريشة</h1>
      <nav>
        <ul>
          <li><a href="index.html">الرئيسية</a></li>
          <li><a href="products.html">المنتجات</a></li>
          <li><a href="cart.html">السلة</a></li>
          <li><a href="login.html">تسجيل الدخول</a></li>
        </ul>
      </nav>
    </div>
  </header>

  <section class="cart">
    <div class="container">
      <h2>سلة الشراء</h2>

      <div class="cart-items"></div>

      <div class="cart-summary">
        <p>الإجمالي: 0 د.أ</p>
        <button class="btn" onclick="window.location.href='checkout.html'">إتمام الدفع</button>
      </div>
    </div>
  </section>

  <footer>
    <div class="container">
      <p>© 2025 جميع الحقوق محفوظة - ريشة</p>
    </div>
  </footer>

  <script>
    function displayCart() {
      const cart = JSON.parse(localStorage.getItem('cart')) || [];
      const cartContainer = document.querySelector('.cart-items');
      let total = 0;

      if (cart.length === 0) {
        cartContainer.innerHTML = '<p>سلتك فارغة</p>';
        return;
      }

      cartContainer.innerHTML = '';
      cart.forEach((item, index) => {
        total += item.price;
        cartContainer.innerHTML += `
          <div class="cart-item">
            <img src="shirt.jpg" alt="${item.name}" />
            <div class="item-details">
              <h3>${item.name}</h3>
              <p>السعر: ${item.price} د.أ</p>
              <button class="remove-btn" data-index="${index}">إزالة</button>
            </div>
          </div>
        `;
      });

      document.querySelector('.cart-summary p').innerHTML = `الإجمالي: ${total.toFixed(2)} د.أ`;

      document.querySelectorAll('.remove-btn').forEach(button => {
        button.addEventListener('click', (e) => {
          const index = e.target.getAttribute('data-index');
          removeFromCart(index);
        });
      });
    }

    function removeFromCart(index) {
      const cart = JSON.parse(localStorage.getItem('cart')) || [];
      cart.splice(index, 1);
      localStorage.setItem('cart', JSON.stringify(cart));
      displayCart();
    }

    displayCart();
  </script>

</body>
</html>
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>تسجيل الدخول - ريشة</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <header>
    <div class="container">
      <h1 class="logo">🧥 ريشة</h1>
      <nav>
        <ul>
          <li><a href="index.html">الرئيسية</a></li>
          <li><a href="products.html">المنتجات</a></li>
          <li><a href="cart.html">السلة</a></li>
          <li><a href="login.html">تسجيل الدخول</a></li>
        </ul>
      </nav>
    </div>
  </header>

  <section class="login">
    <div class="container">
      <h2>تسجيل الدخول</h2>
      <form>
        <label for="email">البريد الإلكتروني:</label>
        <input type="email" id="email" name="email" required />

        <label for="password">كلمة المرور:</label>
        <input type="password" id="password" name="password" required />

        <button type="submit" class="btn">دخول</button>
      </form>
    </div>
  </section>

  <footer>
    <div class="container">
      <p>© 2025 جميع الحقوق محفوظة - ريشة</p>
    </div>
  </footer>

</body>
</html>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f4f4f4;
}

.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
}

header {
  background-color: #333;
  color: white;
  padding: 10px 0;
}

header .logo {
  font-size: 24px;
}

header nav ul {
  list-style: none;
  display: flex;
  gap: 20px;
}

header nav a {
  color: white;
  text-decoration: none;
}

.hero {
  background-color: #ff4081;
  color: white;
  padding: 50px 0;
  text-align: center;
}

.hero .btn {
  background-color: #fff;
  color: #ff4081;
  padding: 10px 20px;
  text-decoration: none;
  border-radius: 5px;
}

footer {
  background-color: #333;
  color: white;
  padding: 10px 0;
  text-align: center;
}

.product-list {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
}

.product {
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  width: calc(33.333% - 20px);
  text-align: center;
}

.product img {
  max-width: 100%;
  height: auto;
}

.product .add-to-cart-btn {
  background-color: #ff4081;
  color: white;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
}

.cart-items {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.cart-item {
  display: flex;
  gap: 20px;
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.cart-item img {
  max-width: 100px;
}

.cart-summary {
  margin-top: 20px;
  text-align: center;
}

.cart-summary .btn {
  background-color: #ff4081;
  color: white;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}
