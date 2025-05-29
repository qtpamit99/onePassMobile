# Test info

- Name: Demoblaze Purchase Flow >> should login, add items to cart, and complete purchase
- Location: C:\Users\Amitu\Playwright_Automation\tests\purchaseFlow.spec.js:11:3

# Error details

```
Error: page.textContent: Test timeout of 60000ms exceeded.
Call log:
  - waiting for locator('.sweet-alert h2')

    at OrderPage.getConfirmationMessage (C:\Users\Amitu\Playwright_Automation\pages\OrderPage.js:34:28)
    at C:\Users\Amitu\Playwright_Automation\tests\purchaseFlow.spec.js:41:34
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
        - /url: cart.html
    - listitem
    - listitem:
      - link "Log out":
        - /url: "#"
    - listitem:
      - link "Welcome pavanol":
        - /url: "#"
    - listitem
  - list:
    - listitem
    - listitem
    - listitem
  - img "First slide"
  - button "Previous"
  - button "Next"
- link "CATEGORIES":
  - /url: ""
- link "Phones":
  - /url: "#"
- link "Laptops":
  - /url: "#"
- link "Monitors":
  - /url: "#"
- link:
  - /url: prod.html?idp_=1
- heading "Samsung galaxy s6" [level=4]:
  - link "Samsung galaxy s6":
    - /url: prod.html?idp_=1
- heading "$360" [level=5]
- paragraph: The Samsung Galaxy S6 is powered by 1.5GHz octa-core Samsung Exynos 7420 processor and it comes with 3GB of RAM. The phone packs 32GB of internal storage cannot be expanded.
- link:
  - /url: prod.html?idp_=2
- heading "Nokia lumia 1520" [level=4]:
  - link "Nokia lumia 1520":
    - /url: prod.html?idp_=2
- heading "$820" [level=5]
- paragraph: The Nokia Lumia 1520 is powered by 2.2GHz quad-core Qualcomm Snapdragon 800 processor and it comes with 2GB of RAM.
- link:
  - /url: prod.html?idp_=3
- heading "Nexus 6" [level=4]:
  - link "Nexus 6":
    - /url: prod.html?idp_=3
- heading "$650" [level=5]
- paragraph: The Motorola Google Nexus 6 is powered by 2.7GHz quad-core Qualcomm Snapdragon 805 processor and it comes with 3GB of RAM.
- link:
  - /url: prod.html?idp_=4
- heading "Samsung galaxy s7" [level=4]:
  - link "Samsung galaxy s7":
    - /url: prod.html?idp_=4
- heading "$800" [level=5]
- paragraph: The Samsung Galaxy S7 is powered by 1.6GHz octa-core it comes with 4GB of RAM. The phone packs 32GB of internal storage that can be expanded up to 200GB via a microSD card.
- link:
  - /url: prod.html?idp_=5
- heading "Iphone 6 32gb" [level=4]:
  - link "Iphone 6 32gb":
    - /url: prod.html?idp_=5
- heading "$790" [level=5]
- paragraph: It comes with 1GB of RAM. The phone packs 16GB of internal storage cannot be expanded. As far as the cameras are concerned, the Apple iPhone 6 packs a 8-megapixel primary camera on the rear and a 1.2-megapixel front shooter for selfies.
- link:
  - /url: prod.html?idp_=6
- heading "Sony xperia z5" [level=4]:
  - link "Sony xperia z5":
    - /url: prod.html?idp_=6
- heading "$320" [level=5]
- paragraph: Sony Xperia Z5 Dual smartphone was launched in September 2015. The phone comes with a 5.20-inch touchscreen display with a resolution of 1080 pixels by 1920 pixels at a PPI of 424 pixels per inch.
- link:
  - /url: prod.html?idp_=7
- heading "HTC One M9" [level=4]:
  - link "HTC One M9":
    - /url: prod.html?idp_=7
- heading "$700" [level=5]
- paragraph: The HTC One M9 is powered by 1.5GHz octa-core Qualcomm Snapdragon 810 processor and it comes with 3GB of RAM. The phone packs 32GB of internal storage that can be expanded up to 128GB via a microSD card.
- link:
  - /url: prod.html?idp_=8
- heading "Sony vaio i5" [level=4]:
  - link "Sony vaio i5":
    - /url: prod.html?idp_=8
- heading "$790" [level=5]
- paragraph: Sony is so confident that the VAIO S is a superior ultraportable laptop that the company proudly compares the notebook to Apple's 13-inch MacBook Pro. And in a lot of ways this notebook is better, thanks to a lighter weight.
- link:
  - /url: prod.html?idp_=9
- heading "Sony vaio i7" [level=4]:
  - link "Sony vaio i7":
    - /url: prod.html?idp_=9
- heading "$790" [level=5]
- paragraph: REVIEW Sony is so confident that the VAIO S is a superior ultraportable laptop that the company proudly compares the notebook to Apple's 13-inch MacBook Pro. And in a lot of ways this notebook is better, thanks to a lighter weight, higher-resolution display, more storage space, and a Blu-ray drive.
- list:
  - listitem:
    - button "Previous"
  - listitem:
    - button "Next"
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
   1 | class OrderPage {
   2 |   constructor(page) {
   3 |     this.page = page;
   4 |     this.orderModal = '#orderModal';
   5 |     this.nameField = '#name';
   6 |     this.countryField = '#country';
   7 |     this.cityField = '#city';
   8 |     this.cardField = '#card';
   9 |     this.monthField = '#month';
  10 |     this.yearField = '#year';
  11 |     this.purchaseButton = 'button[onclick="purchaseOrder()"]';
  12 |     this.confirmationModal = '.sweet-alert';
  13 |     this.confirmationMessage = '.sweet-alert h2';
  14 |     this.okButton = 'button.confirm:has-text("OK")';
  15 |   }
  16 |
  17 |   async fillPurchaseDetails(details) {
  18 |     await this.page.waitForSelector(this.orderModal, { state: 'visible' });
  19 |     await this.page.fill(this.nameField, details.name);
  20 |     await this.page.fill(this.countryField, details.country);
  21 |     await this.page.fill(this.cityField, details.city);
  22 |     await this.page.fill(this.cardField, details.card);
  23 |     await this.page.fill(this.monthField, details.month);
  24 |     await this.page.fill(this.yearField, details.year);
  25 |   }
  26 |
  27 |   async confirmPurchase() {
  28 |     await this.page.click(this.purchaseButton);
  29 |     await this.page.waitForSelector(this.confirmationModal, { state: 'visible' });
  30 |     await this.page.click(this.okButton);
  31 |   }
  32 |
  33 |   async getConfirmationMessage() {
> 34 |     return await this.page.textContent(this.confirmationMessage);
     |                            ^ Error: page.textContent: Test timeout of 60000ms exceeded.
  35 |   }
  36 | }
  37 |
  38 | module.exports = { OrderPage };
```