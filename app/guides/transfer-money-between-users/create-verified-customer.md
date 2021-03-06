---
layout: twoColumn
section: guides
type: guide
guide:
    name: transfer-money-between-users
    step: '2'
title:  Creating A Verified Customer
description: When the customer is created, you’ll receive the customer URL in the location header.
---
# Step 2: Create a Verified Customer

First, we’ll create a `Verified Customer` for Jane Merchant.

There are two types of verified Customers you can create; [Personal Verified Customers](https://developers.dwolla.com/resources/personal-verified-customer.html) and [Business Verified Customers.](https://developers.dwolla.com/resources/business-verified-customer.html) In this example, we use [business verified customers](https://developers.dwolla.com/resources/business-verified-customer.html) (sole proprietorship) to represent the merchant who will be receiving funds.

```raw
POST https://api-sandbox.dwolla.com/customers
Content-Type: application/vnd.dwolla.v1.hal+json
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer 0Sn0W6kzNic+oWhDbQcVSKLRUpGjIdl/YyrHqrDDoRnQwE7Q

{
    "firstName": "Jane",
    "lastName": "Merchant",
    "email": "solePropBusiness@email.com",
    "ipAddress": "143.156.7.8",
    "type": "business",
    "dateOfBirth": "1980-01-31",
    "ssn": "6789",
    "address1": "99-99 33rd St",
    "city": "Some City",
    "state": "NY",
    "postalCode": "11101",
    "businessClassification": "9ed3f670-7d6f-11e3-b1ce-5404a6144203",
    "businessType": "soleProprietorship",
    "businessName":"Jane Corp",
    "ein":"00-0000000"
}

HTTP/1.1 201 Created
Location: https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5
```

```php
<?php
$customersApi = new DwollaSwagger\CustomersApi($apiClient);
$new_customer = 'https://api-sandbox.dwolla.com/customers/b70c3194-35fa-49e8-9243-d55a30e06d1e';
$new_customer = $customersApi->create([
    'firstName' => 'Jane',
    'lastName' => 'Merchant',
    'email' => 'solePropBusiness@email.com',
    'ipAddress' => '143.156.7.8',
    'type' => 'business',
    'dateOfBirth' => '1980-01-31',
    'ssn' => '6789',
    'address1' => '99-99 33rd St',
    'city' => 'Some City',
    'state' => 'NY',
    'postalCode' => '11101',
    'businessClassification' => '9ed3f670-7d6f-11e3-b1ce-5404a6144203',
    'businessType' => 'soleProprietorship',
    'businessName' => 'Jane Corp',
    'ein' => '00-0000000']);

?>
```

```ruby
# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby (Recommended)
request_body = {
    :firstName => 'Jane',
    :lastName => 'Merchant',
    :email => 'solePropBusiness@email.com',
    :ipAddress => '143.156.7.8',
    :type => 'business',
    :dateOfBirth => '1980-01-31',
    :ssn => '6789',
    :address1 => '99-99 33rd St',
    :city => 'Some City',
    :state => 'NY',
    :postalCode => '11101',
    :businessClassification => '9ed3f670-7d6f-11e3-b1ce-5404a6144203',
    :businessType => 'soleProprietorship',
    :businessName => 'Jane Corp',
    :ein => '00-0000000'
}

customer = app_token.post "customers", request_body
customer.response_headers[:location] # => "https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5"
```

```python
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python (Recommended)
request_body = {
  'firstName': 'Jane',
  'lastName': 'Merchant',
  'email': 'solePropBusiness@email.com',
  'ipAddress': '143.156.7.8',
  'type': 'business',
  'dateOfBirth': '1980-01-31',
  'ssn': '6789',
  'address1': '99-99 33rd St',
  'city': 'Some City',
  'state': 'NY',
  'postalCode': '11101',
  'businessClassification': '9ed3f670-7d6f-11e3-b1ce-5404a6144203',
  'businessType': 'soleProprietorship',
  'businessName': 'Jane Corp',
  'ein': '00-0000000'
}

customer = app_token.post('customers', request_body)
customer.headers['location'] # => 'https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5'
```

```javascript
var requestBody = {
    firstName: 'Jane',
    lastName: 'Merchant',
    email: 'solePropBusiness@email.com',
    ipAddress: '143.156.7.8',
    type: 'business',
    dateOfBirth: '1980-01-31',
    ssn: '6789',
    address1: '99-99 33rd St',
    city: 'Some City',
    state: 'NY',
    postalCode: '11101',
    businessClassification: '9ed3f670-7d6f-11e3-b1ce-5404a6144203',
    businessType: 'soleProprietorship',
    businessName: 'Jane Corp',
    ein: '00-0000000',
};

appToken
  .post('customers', requestBody)
  .then(res => res.headers.get('location')); // => 'https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5'
```

When the customer is created, you’ll receive the customer URL in the location header.

**Important:** There are various reasons a Verified Customer will result in a status other than `verified` which you will want to account for after the Customer is created. Reference the Customer verification resource article for more information on [handling verification statuses](https://developers.dwolla.com/resources/customer-verification/handling-verification-statuses.html).

<nav class="pager-nav">
    <a href="./obtain-access-token.html">Back: Obtain an access token</a>
    <a href="attach-unverified-bank.html">Next: Attach an unverified funding source</a>
</nav>
