# API

### **Obtaining the API Key**

To obtain the API key:

1. Navigate to the **Settings** page in the **Staff Panel**.
2. Scroll down to the **API Settings** section.
3. Ensure the **Enable API** checkbox is checked.
4. Set your desired API key in the input field labeled "Enter API Key".
5. Save the settings by clicking the **Save Settings** button.

{% hint style="warning" %}
The API key is private and should not be shared with anyone. It can be any string you choose, but it’s important to make sure it’s secure (e.g., a long and complex password-like string).
{% endhint %}





***

### Endpoint: `/api/users/:userId` (GET)

This API endpoint allows you to retrieve detailed information about a user based on their Discord ID. The data returned includes user information, the contents of their cart, and the products/serials they own.

#### URL Parameters

* **userID** (string): The Discord ID or User ID of the user whose information you want to retrieve.

#### Headers

* **x-api-key** (string): This is required for authentication. The API key must be included in the header to access this endpoint.

#### Success Response

* **Status Code:** `200 OK`
* **Response Body:**

```json
{
  "id": "123456789012345678",
  "discordID": "123456789012345678",
  "userId": "507f1f77bcf86cd799439011",
  "username": "JohnDoe",
  "displayName": "JohnDoe",
  "banned": false,
  "email": "user@example.com",
  "emailVerified": true,
  "totalSpent": 150.00,
  "joinedAt": "2024-01-15T14:56:29.000Z",
  "authMethod": "discord",
  "cart": [
    {
      "_id": "507f191e810c19729de860ea",
      "name": "Product 1",
      "productType": "digitalPaid"
    },
    {
      "_id": "507f191e810c19729de860eb",
      "name": "Product 2",
      "productType": "digitalFree"
    }
  ],
  "ownedProducts": [
    {
      "_id": "507f191e810c19729de860ec",
      "name": "Paid product",
      "productType": "digitalPaid"
    },
    {
      "_id": "507f191e810c19729de860ed",
      "name": "Free product",
      "productType": "digitalFree"
    },
    {
      "_id": "507f191e810c19729de860ed",
      "name": "Service product",
      "productType": "service"
    }
  ],
  "ownedSerials": [
    {
      "productId": "507f191e810c19729de860ec",
      "productName": "Premium License",
      "key": "XXXX-XXXX-XXXX-XXXX",
      "purchaseDate": "2024-01-20T10:30:00.000Z"
    }
  ]
}
```

#### Possible Error Responses:

```json
{
  "error": "INVALID_API_KEY"
}
{
  "error": "USER_NOT_FOUND"
}
{
  "error": "SERVER_ERROR"
}
```

#### Axios Example:

```javascript
const axios = require('axios');

const getUserData = async (userId) => {
  try {
    const response = await axios.get(`https://your-api-domain.com/api/users/${userId}`, {
      headers: {
        'x-api-key': 'your-api-key'  // Replace with your actual API key
      }
    });
    console.log('User Data:', response.data);
  } catch (error) {
    // Handle the error simply
    console.error('Error fetching user data:', error.response ? error.response.data : error.message);
  }
};

getUserData('123456789012345678');  // Replace with the actual Discord User ID
```



***

### Endpoint: `/api/users/:userId/addproduct/:urlId` (POST)

This API endpoint allows you to add a specific product to a user's owned products list based on their Discord ID and the product's unique `urlId`.

#### URL Parameters

* **`userId`(string)**:\
  The Discord ID or User ID of the user to whom the product should be added.
* **`urlId` (string)**:\
  The unique identifier for the product to be added. This is typically a URL-safe string such as `product-name`.

#### Headers

* **x-api-key** (string): This is required for authentication. The API key must be included in the header to access this endpoint.

#### Success Response

* **Status Code:** `200 OK`
* **Response Body:**

```json
{
  "message": "PRODUCT_ADDED_SUCCESSFULLY",
  "user": {
    "id": "123456789012345678",
    "discordID": "123456789012345678",
    "email": "user@example.com",
    "authMethod": "discord",
    "ownedProducts": [ // A list of all products the user owns
      {
        "_id": "507f191e810c19729de860ea",
        "name": "Premium Package",
        "productType": "digitalPaid",
        "urlId": "premium-package"
      },
      {
        "_id": "507f191e810c19729de860eb",
        "name": "Test Product",
        "productType": "digitalPaid",
        "urlId": "test-product"
      }
    ]
  },
  "product": { // The product that was added
    "name": "Test Product",
    "urlId": "test-product"
  }
}
```

#### Possible Error Responses:

```json
{
  "error": "INVALID_API_KEY"
}
{
  "error": "USER_NOT_FOUND"
}
{
  "error": "PRODUCT_NOT_FOUND"
}
{
  "error": "PRODUCT_ALREADY_OWNED"
}
{
  "error": "SERVER_ERROR"
}
```

#### Axios Example:

```javascript
const axios = require('axios');

const addProductToUser = async (userId, urlId) => {
  try {
    const response = await axios.post(`https://your-api-domain.com/api/users/${userId}/addproduct/${urlId}`, {}, {
      headers: {
        'x-api-key': 'your-api-key' // Replace with your actual API key
      }
    });
    console.log('Product Added:', response.data);
  } catch (error) {
    // Handle the error
    console.error('Error adding product to user:', error.response ? error.response.data : error.message);
  }
};

// Example usage
addProductToUser('123456789', 'test-product'); // Replace with the actual Discord User ID and product urlId
```

***

### Endpoint: `/api/users/:userId/removeproduct/:urlId` (POST)

This API endpoint allows you to remove a specific product from a user's owned products list based on their Discord ID and the product's unique `urlId`.

#### URL Parameters

* **`userId`(string)**:\
  The Discord ID or User ID of the user to whom the product should be added.
* **`urlId` (string)**:\
  The unique identifier for the product to be added. This is typically a URL-safe string such as `product-name`.

#### Headers

* **x-api-key** (string): This is required for authentication. The API key must be included in the header to access this endpoint.

#### Success Response

* **Status Code:** `200 OK`
* **Response Body:**

```json
{
  "message": "PRODUCT_REMOVED_SUCCESSFULLY",
  "user": {
    "id": "123456789012345678",
    "discordID": "123456789012345678",
    "email": "user@example.com",
    "authMethod": "discord",
    "ownedProducts": [ // A list of all products the user owns
      {
        "_id": "507f191e810c19729de860ea",
        "name": "Premium Package",
        "productType": "digitalPaid",
        "urlId": "premium-package"
      }
    ]
  },
  "product": { // The product that was removed
    "name": "Test Product",
    "urlId": "test-product"
  }
}
```

#### Possible Error Responses:

```json
{
  "error": "INVALID_API_KEY"
}
{
  "error": "USER_NOT_FOUND"
}
{
  "error": "PRODUCT_NOT_FOUND"
}
{
  "error": "PRODUCT_NOT_OWNED"
}
{
  "error": "SERVER_ERROR"
}
```

#### Axios Example:

```javascript
const axios = require('axios');

const removeProductFromUser = async (userId, urlId) => {
  try {
    const response = await axios.post(`https://your-api-domain.com/api/users/${userId}/removeproduct/${urlId}`, {}, {
      headers: {
        'x-api-key': 'your-api-key' // Replace with your actual API key
      }
    });
    console.log('Product Removed:', response.data);
  } catch (error) {
    // Handle the error
    console.error('Error removing product from user:', error.response ? error.response.data : error.message);
  }
};

// Example usage
removeProductFromUser('123456789', 'test-product'); // Replace with the actual Discord User ID and product urlId
```

***

### Endpoint: `/api/discounts/create` (POST)

This API endpoint allows you to create a new discount code for your store, specifying its name, discount percentage, maximum uses, and expiration date.

#### **Request Body**

| Field                | Type   | Required | Description                                                                        |
| -------------------- | ------ | -------- | ---------------------------------------------------------------------------------- |
| `name`               | string | Yes      | The unique name of the discount code.                                              |
| `discountPercentage` | number | Yes      | The percentage discount (e.g., `10` for a 10% discount).                           |
| `maxUses`            | number | No       | The maximum number of times the code can be used. Leave empty for unlimited.       |
| `expiresAt`          | string | No       | The expiration date of the code in ISO 8601 format. Leave empty for no expiration. |

#### Headers

* **x-api-key** (string): This is required for authentication. The API key must be included in the header to access this endpoint.

#### Success Response

* **Status Code:** `200 OK`
* **Response Body:**

```json
{
  "message": "DISCOUNT_CODE_CREATED_SUCCESSFULLY",
  "discountCode": {
    "name": "NEWYEAR2025",
    "discountPercentage": 20,
    "maxUses": 100,
    "expiresAt": "2025-12-31T23:59:59.000Z"
  }
}
```

#### Possible Error Responses:

```json
{
  "error": "INVALID_API_KEY"
}
{
  "error": "DISCOUNT_CODE_ALREADY_EXISTS"
}
{
  "error": "SERVER_ERROR"
}
```

#### Axios Example:

```javascript
const axios = require('axios');

const createDiscountCode = async () => {
  try {
    const response = await axios.post(
      'https://your-api-domain.com/api/discounts/create',
      {
        name: 'NEWYEAR2025',
        discountPercentage: 20,
        maxUses: 100,
        expiresAt: '2025-12-31T23:59:59.000Z'
      },
      {
        headers: {
          'x-api-key': 'your-api-key' // Replace with your actual API key
        }
      }
    );
    console.log('Discount Code Created:', response.data);
  } catch (error) {
    console.error('Error creating discount code:', error.response ? error.response.data : error.message);
  }
};

// Example usage
createDiscountCode();
```



***

### Endpoint: `/api/payments/:transactionID` (GET)

This API endpoint allows you to retrieve detailed payment information based on a specific transaction ID. The returned data includes details about the payment method, user information, products purchased, and any discounts applied.

#### URL Parameters

* **transactionID** (string): The unique transaction ID associated with the payment you want to retrieve.

#### Headers

* **x-api-key** (string): This is required for authentication. The API key must be included in the header to access this endpoint.

#### Success Response

* **Status Code:** `200 OK`
* **Response Body:**

```json
{
  "ID": 12345,
  "transactionID": "abcd1234efgh5678",
  "paymentMethod": "paypal", // paypal or stripe or coinbase
  "userID": "123456789012345678",
  "username": "discordUsername",
  "email": "john@example.com",
  "products": [ // the products purchased
    {
      "name": "Product 1",
      "price": 29.99
    },
    {
      "name": "Product 2",
      "price": 49.99
    }
  ],
  "discountCode": "SUMMER2024",
  "discountPercentage": 10,
  "createdAt": "2024-08-15T14:56:29.000Z"
}
```

#### Possible Error Responses:

```json
{
  "error": "INVALID_API_KEY"
}
{
  "error": "PAYMENT_NOT_FOUND"
}
{
  "error": "SERVER_ERROR"
}
```

#### Axios Example:

```javascript
const axios = require('axios');

const getPaymentData = async (transactionID) => {
  try {
    const response = await axios.get(`https://your-api-domain.com/api/payments/${transactionID}`, {
      headers: {
        'x-api-key': 'your-api-key'  // Replace with your actual API key
      }
    });
    console.log('Payment Data:', response.data);
  } catch (error) {
    // Handle the error simply
    console.error('Error fetching payment data:', error.response ? error.response.data : error.message);
  }
};

getPaymentData('abcd1234efgh5678');  // Replace with the actual Transaction ID
```

***

### Endpoint: `/api/products` (GET)

This API endpoint allows you to retrieve detailed information about all products available in the system. The data returned includes the product's name, type, price, total purchases, total earned, total downloads, and creation date.

#### Headers

* **x-api-key** (string): This is required for authentication. The API key must be included in the header to access this endpoint.

#### Success Response

* **Status Code:** `200 OK`
* **Response Body:**

```json
[
  {
    "name": "Product 1",
    "productType": "digitalPaid",
    "price": 29.99,
    "description": "This is a paid product.",
    "totalPurchases": 150,
    "totalEarned": 4498.50,
    "totalDownloads": 1200,
    "createdAt": "2023-01-15T14:56:29.000Z"
  },
  {
    "name": "Product 2",
    "productType": "digitalFree",
    "description": "This is a free product.",
    "totalPurchases": 200,
    "totalEarned": 9998.00,
    "totalDownloads": 0,
    "createdAt": "2023-02-10T10:30:00.000Z"
  }
]
```

#### Possible Error Responses:

```json
{
  "error": "INVALID_API_KEY"
}
{
  "error": "NO_PRODUCTS_FOUND"
}
{
  "error": "SERVER_ERROR"
}
```

#### Axios Example:

```javascript
const axios = require('axios');

const getProducts = async () => {
  try {
    const response = await axios.get('https://your-api-domain.com/api/products', {
      headers: {
        'x-api-key': 'your-api-key'  // Replace with your actual API key
      }
    });
    console.log('Products:', response.data);
  } catch (error) {
    // Handle the error simply
    console.error('Error fetching products:', error.response ? error.response.data : error.message);
  }
};

getProducts();  // Fetch all products
```



***

### Endpoint: `/api/statistics` (GET)

This API endpoint provides aggregated statistics about the platform, including total purchases, total earnings, total site visits, as well as the total number of users and products.

#### Headers

* **x-api-key** (string): This is required for authentication. The API key must be included in the header to access this endpoint.

#### Success Response

* **Status Code:** `200 OK`
* **Response Body:**

```json
{
  "totalPurchases": 5000,
  "totalEarned": 150000.00,
  "totalSiteVisits": 200000,
  "totalUsers": 1200,
  "totalProducts": 300
}
```

#### Possible Error Responses:

```json
{
  "error": "INVALID_API_KEY"
}
{
  "error": "STATISTICS_NOT_FOUND"
}
{
  "error": "SERVER_ERROR"
}
```

#### Axios Example:

```javascript
const axios = require('axios');

const getStatistics = async () => {
  try {
    const response = await axios.get('https://your-api-domain.com/api/statistics', {
      headers: {
        'x-api-key': 'your-api-key'  // Replace with your actual API key
      }
    });
    console.log('Statistics:', response.data);
  } catch (error) {
    // Handle the error simply
    console.error('Error fetching statistics:', error.response ? error.response.data : error.message);
  }
};

getStatistics();  // Fetch platform statistics
```



***

### Endpoint: `/api/reviews` (GET)

This API endpoint allows you to retrieve all reviews submitted by users. Each review includes the user's Discord ID, the name of the product reviewed, the rating, the comment, and the creation date.

#### Headers

* **x-api-key** (string): This is required for authentication. The API key must be included in the header to access this endpoint.

#### Success Response

* **Status Code:** `200 OK`
* **Response Body:**

```json
[
  {
    "discordID": "123456789012345678",
    "productName": "Product 1",
    "rating": 5,
    "comment": "Excellent product!",
    "createdAt": "2024-08-15T14:56:29.000Z"
  },
  {
    "discordID": "987654321098765432",
    "productName": "Product 2",
    "rating": 2,
    "comment": "Very good, but could be better.",
    "createdAt": "2024-08-14T10:30:00.000Z"
  }
]
```

#### Possible Error Responses:

```json
{
  "error": "INVALID_API_KEY"
}
{
  "error": "NO_REVIEWS_FOUND"
}
{
  "error": "SERVER_ERROR"
}
```

#### Axios Example:

```javascript
const axios = require('axios');

const getReviews = async () => {
  try {
    const response = await axios.get('https://your-api-domain.com/api/reviews', {
      headers: {
        'x-api-key': 'your-api-key'  // Replace with your actual API key
      }
    });
    console.log('Reviews:', response.data);
  } catch (error) {
    // Handle the error simply
    console.error('Error fetching reviews:', error.response ? error.response.data : error.message);
  }
};

getReviews();  // Fetch all reviews
```
