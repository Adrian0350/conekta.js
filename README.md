![alt tag](https://raw.github.com/conekta/conekta.js/master/readme_files/cover.png)

# Conekta.JS 0.3.1 

## A simple library to tokenize.

Before you get started, you will need to create an account on https://admin.conekta.io.  After creating and activating your company, you will have access to a set of keys (https://admin.conekta.io#developer.keys) which will allow you to begin processing payments.  To get started, include conekta.js (https://s3.amazonaws.com/conektaapi/v0.2.0/js/conekta.js) on your page and set your public keys:

    Conekta.setPublishableKey('xxxxxxxxxxxxxxxx');

To start processing credit cards do this:
```js
Conekta.charge.new({
  amount:10000,
  currency:'MXN',
  description:'Double-black belt'
  card:{
    name:'Bruce Lee',
    number:'4111111111111111',
    exp_year:'12',
    exp_month:'04',
    cvv:'123',
  }
},
  function(charge){
    alert('Success!');
  },
  function(response){
    alert('Fail!');
  }
);
```

For oxxo:
```js
Conekta.charge.new(
  {
    amount:10000,
    currency:'MXN',
    description:'Double-black belt'
    cash:{
      type:'oxxo'
    }
  }, 
  function(charge){
    $('#my-oxxo-barcode-tag').attr('src', charge.payment_method.barcode_url);
  },
  function(error){
    alert('Fail!');
  }
);
```

For bank_transfers:
```js
Conekta.charge.new(
  {
    amount:10000,
    currency:'MXN',
    description:'Double-black belt'
    bank:{
      type:'banorte'
    }
  }, 
  function(charge){
    $('#my-bank-transfer-bank-name-tag').attr('src', charge.payment_method.bank);
    $('#my-bank-transfer-service-name-tag').attr('src', charge.payment_method.service_name);
    $('#my-bank-transfer-service-id-tag').attr('src', charge.payment_method.service_id);
    $('#my-bank-transfer-reference-tag').attr('src', charge.payment_method.reference);
  },
  function(error){
    alert('Fail!');
  }
);
```

License
-------
Developed by [Conekta](https://www.conekta.io). Available with [MIT License](LICENSE).
