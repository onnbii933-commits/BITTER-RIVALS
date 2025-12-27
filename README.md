# BITTER-RIVALS
WARZONE<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Bitter Rivals – Ebook ($4)</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<script src="https://www.paypal.com/sdk/js?client-id=AZUM4-zdiX8ZTDZZJT9LPrGjJzp_XesZ7H0PDTS9Ggge2XdEszhdPiKV2eWGqWdLI9a8e0Xc2HQzSBMI&currency=USD"></script>

<style>
body {
    background:#0e0e0e;
    color:#fff;
    font-family:Arial;
    text-align:center;
    padding:20px;
}
.container {
    max-width:700px;
    margin:auto;
}
.price {
    font-size:30px;
    font-weight:bold;
    color:#00ff9c;
    margin:15px 0;
}
img {
    width:230px;
    border-radius:12px;
    margin-top:20px;
}
</style>
</head>

<body>

<div class="container">
    <h1>Bitter Rivals – Ebook (PDF)</h1>
    <div class="price">$4.00 USD</div>

    <img src="images/cover.jpg" alt="Book Cover">

    <p>Pay once and download instantly.</p>

    <div id="paypal-button-container"></div>
</div>

<script>
paypal.Buttons({
    createOrder: (data, actions) => {
        return actions.order.create({
            purchase_units: [{
                amount: { value: "4.00" }
            }]
        });
    },
    onApprove: (data, actions) => {
        return actions.order.capture().then(() => {
            window.location.href = "download.html";
        });
    }
}).VERCEL('#paypal-button-container');
</script>

</body>
</html>


