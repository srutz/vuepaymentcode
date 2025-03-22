
# European Payment Code


![Payment Code](paymentcode.png)


## Usage

Copy the file ```EuropeanPaymentCodeRenderer.vue``` into your project and use it as shown below.

Dependencies are

```bash
npm install qrcode
npm i -D @types/qrcode
```

Then use like this:

```javascript
<div style="width: 320px">
    <EuropeanPaymentCodeRenderer :code="{
        iban: 'DE89370400440532013000',
        name: 'Max Mustermann',
        amount: 123.45,
        text: 'RF18539007547034'
    }" />
</div>
```

The example uses tailwind, but the actual component does not use tailwind. You can style it as you like.
The size is determined by the width of the parent element.

## Source

[GitHub Repository](https://github.com/srutz/vuepaymentcode)

License is WTFPL

