# Nebula

Nebula is the API REST to handle unique and recurrent payments.


# **POST   /services/paynow**
## Body:
```js
{
  "paynow": {
    "person_id": "per_XXXXXXXXXX",            // Mandatory field. Must be a valid person_id.
    "amount": 3562.5,                         // Mandatory field. Must be a number greater than 1.
    "concept": "Pago de HM",                  // Mandatory field. Just explain the reason for the transaction.
    "currency": "MXN",                        // Mandatory field. Must be a valid ISO_CODE (MXN, USD, ...)
    "method_id": "card",                      // Mandatory field. Values could be "oxxo", "7eleven", "card", etc.
    "campaign_id": "camp_DFfUVJ3SIHO3u",      // Optional field. Must be a valid campaign_id.
    "subscription_id": "subs_mb7fpcg6f84fc",  // Optional field.
    "card": {
           // See below for details on this field.
    },
    "user_id": "usr_A0CZsoXMfPebeB"          // Optional field. Must be a valid user_id.
    "geolocation": {                         // Optional field.
      "lat":  XXXXXXXXXXX
      "lng":  XXXXXXXXXXXXXXX
    },
    "metadata": {                            // Optional field
      // Any extra data needed
      "XXXXX": "XXXXXXXX"
    },
    "data_1": "oy data_1",
    "data_2": "soy data_2",
    "data_3": "soy asgyhsklmnabsgiyughasdiklgb",
    "device_fingerprint": "sdf54dsf5s4dfsd5f4dsf54sdfeghy"   // Optional field
  }
}
```
# Card field on body request:

## **It can only be in one of these ways:**

### 1- Use this way if you have access to the card_id in our DB, otherwise, continue reading.

```js
 {
    "id": "card_XXXXXXXXXX"     // Must be a valid card_id.
 }
```

### 2- Use this way if you have the card information, like number, cvv, expiration date, etc.

```js
 {
    "number": "4024007115987413",        // Must be a valid credit card number.
    "cardholder":"Recaudia",    
    "exp_month": "12",                   // Must be only two digits.
    "exp_year": "2017",                  // Must be only two digits.
    "cvv": "311"                         // Must be a valid cvv number.
 }
```

