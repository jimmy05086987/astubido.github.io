<!DOCTYPE html>
<html>
<head>
    <title>飲料店點餐系統<\/title>
<\/head>
<body>
    <h1>歡迎來到我們的飲料店！請點擊您想要的飲料：<\/h1>
    <form id="orderForm">
        <input type="checkbox" name="drink" value="珍珠奶茶">珍珠奶茶<br>
        <input type="checkbox" name="drink" value="水果茶">水果茶<br>
        <input type="checkbox" name="drink" value="冰沙">冰沙<br>
    <\/form>
    <button onclick="submitOrder()">提交訂單<\/button>

    <h2>您的訂單：<\/h2>
    <ul id="orderList"><\/ul>

    <script src="script.js"><\/script>
<\/body>
<\/html>
```

JavaScript部分（儲存為`script.js`）：
```javascript
function submitOrder() {
    var orderForm = document.getElementById("orderForm");
    var orderList = document.getElementById("orderList");
    var selectedDrinks = orderForm.querySelectorAll('input[name="drink"]:checked');

    if (selectedDrinks.length === 0) {
        alert("請選擇至少一種飲料！");
        return;
    }

    orderList.innerHTML = "";

    for (var i = 0; i < selectedDrinks.length; i++) {
        var drink = document.createElement("li");
        drink.appendChild(document.createTextNode(selectedDrinks[i].value));
        orderList.appendChild(drink);
    }

    alert("訂單已提交！");
    orderForm.reset();
}
