# BITTER-RIVALS
WARZONE
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Bitter Rivals – Ebook</title>

  <!-- PayPal SDK with YOUR Client ID -->
  <script src="https://www.paypal.com/sdk/js?client-id=AZUM4-zdiX8ZTDZZJT9LPrGjJzp_XesZ7H0PDTS9Ggge2XdEszhdPiKV2eWGqWdLI9a8e0Xc2HQzSBMI&currency=USD"></script>

  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
      padding: 40px;
      text-align: center;
    }
    .box {
      background: #fff;
      max-width: 420px;
      margin: auto;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    input {
      width: 90%;
      padding: 10px;
      margin-bottom: 15px;
    }
  </style>
</head>

<body>

<div class="box">
  <h1>Bitter Rivals</h1>
  <p><strong>Price:</strong> $4.00</p>
  <p>Instant PDF download after payment</p>

  <input id="email" type="email" placeholder="Your email address" required>

  <div id="paypal-button-container"></div>
</div>

<script>
paypal.Buttons({
  createOrder: function () {
    return fetch("/api/create-order")
      .then(res => res.json())
      .then(data => data.id);
  },

  onApprove: function (data) {
    return fetch("/api/capture-order", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({
        orderID: data.orderID,
        email: document.getElementById("email").value
      })
    })
    .then(res => res.json())
    .then(data => {
      window.location.href = "success.html?token=" + data.token;
    });
  }
}).render("#paypal-button-container");
</script>

</body>
</html>
