# Test info

- Name: Demoblaze Purchase Flow >> should login, add items to cart, and complete purchase
- Location: C:\Users\Amitu\Playwright_Automation\tests\purchaseFlow.spec.js:10:3

# Error details

```
Error: expect(received).toContain(expected) // indexOf

Expected value: "Sony xperia z5"
Received array: ["Nokia lumia 1520", "Samsung galaxy s6", "Sony vaio i5", "HTC One M9"]
    at C:\Users\Amitu\Playwright_Automation\tests\purchaseFlow.spec.js:33:25
```

# Page snapshot

```yaml
- navigation:
  - link "PRODUCT STORE":
    - /url: index.html
    - img
    - text: PRODUCT STORE
  - list:
    - listitem:
      - link "Home (current)":
        - /url: index.html
    - listitem:
      - link "Contact":
        - /url: "#"
    - listitem:
      - link "About us":
        - /url: "#"
    - listitem:
      - link "Cart":
        - /url: "#"
    - listitem
    - listitem:
      - link "Log out":
        - /url: "#"
    - listitem:
      - link "Welcome pavanol":
        - /url: "#"
    - listitem
- heading "Products" [level=2]
- table:
  - rowgroup:
    - row "Pic Title Price x":
      - cell "Pic"
      - cell "Title"
      - cell "Price"
      - cell "x"
  - rowgroup:
    - row "Nokia lumia 1520 820 Delete":
      - cell:
        - img
      - cell "Nokia lumia 1520"
      - cell "820"
      - cell "Delete":
        - link "Delete":
          - /url: "#"
    - row "Samsung galaxy s6 360 Delete":
      - cell:
        - img
      - cell "Samsung galaxy s6"
      - cell "360"
      - cell "Delete":
        - link "Delete":
          - /url: "#"
    - row "Sony vaio i5 790 Delete":
      - cell:
        - img
      - cell "Sony vaio i5"
      - cell "790"
      - cell "Delete":
        - link "Delete":
          - /url: "#"
    - row "HTC One M9 700 Delete":
      - cell:
        - img
      - cell "HTC One M9"
      - cell "700"
      - cell "Delete":
        - link "Delete":
          - /url: "#"
- heading "Total" [level=2]
- heading "2670" [level=3]
- button "Place Order"
- heading "About Us" [level=4]
- paragraph: We believe performance needs to be validated at every stage of the software development cycle and our open source compatible, massively scalable platform makes that a reality.
- heading "Get in Touch" [level=4]
- paragraph: "Address: 2390 El Camino Real"
- paragraph: "Phone: +440 123456"
- paragraph: "Email: demo@blazemeter.com"
- heading "PRODUCT STORE" [level=4]:
  - img
  - text: PRODUCT STORE
- contentinfo:
  - paragraph: Copyright © Product Store 2017
```

# Test source

```ts
   1 | const { test, expect } = require('@playwright/test');
   2 | const { BaseTest } = require('../utils/baseTest');
   3 | const { LoginPage } = require('../pages/LoginPage');
   4 | const { HomePage } = require('../pages/HomePage');
   5 | const { CartPage } = require('../pages/CartPage');
   6 | const { OrderPage } = require('../pages/OrderPage');
   7 | const testData = require('../test-data/testData.json');
   8 |
   9 | test.describe('Demoblaze Purchase Flow', () => {
  10 |   test('should login, add items to cart, and complete purchase', async ({ page, baseURL }) => {
  11 |     const baseTest = new BaseTest(page);
  12 |     const loginPage = new LoginPage(page);
  13 |     const homePage = new HomePage(page);
  14 |     const cartPage = new CartPage(page);
  15 |     const orderPage = new OrderPage(page);
  16 |
  17 |     // Navigate to homepage
  18 |     await baseTest.navigateTo(baseURL);
  19 |
  20 |     // Login
  21 |     await loginPage.login(testData.userCredentials.username, testData.userCredentials.password);
  22 |     await expect(await loginPage.getWelcomeText()).toContain(testData.userCredentials.username);
  23 |
  24 |     // Add items to cart
  25 |     for (const item of testData.items) {
  26 |       await homePage.addItemToCart(item);
  27 |     }
  28 |
  29 |     // Navigate to cart and verify items
  30 |     await cartPage.navigateToCart();
  31 |     const cartItems = await cartPage.getCartItems();
  32 |     for (const item of testData.items) {
> 33 |       expect(cartItems).toContain(item);
     |                         ^ Error: expect(received).toContain(expected) // indexOf
  34 |     }
  35 |
  36 |     // Complete purchase
  37 |     await cartPage.proceedToPurchase();
  38 |     await orderPage.fillPurchaseDetails(testData.purchaseDetails);
  39 |     await orderPage.confirmPurchase();
  40 |     await expect(await orderPage.getConfirmationMessage()).toBe('Thank you for your purchase!');
  41 |
  42 |     // Verify logout button
  43 |     await expect(await loginPage.isLogoutButtonVisible()).toBe(true);
  44 |   });
  45 | });
```