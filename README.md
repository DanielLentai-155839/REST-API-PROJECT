REST API for Product Management
This is a simple REST API built using Python and Flask to manage a Product resource. The API supports creating, retrieving, updating, and deleting products. A client interaction script is also provided to interact with the API.

Table of Contents
Features
Setup Instructions
API Endpoints
Testing the API
Client Interaction Script
Features
Endpoints:
Add a new product.
Retrieve all products.
Retrieve a product by ID.
Update a product.
Delete a product.
Error Handling:
400 Bad Request: Invalid input data.
404 Not Found: Requested resource does not exist.
201 Created: Product created successfully.
JSON request and response format.
Setup Instructions
1. Prerequisites
Python 3.7+ must be installed.
Install pip for managing Python packages.
2. Install Required Libraries
Run the following command to install Flask and Requests:pip install flask requests
3. Run the API Server
Save the API code to a file named product_api.py.
Start the API server by running:python product_api.py
The server will run on http://127.0.0.1:5000.

Here's the content for your README.md file:

REST API for Product Management
This is a simple REST API built using Python and Flask to manage a Product resource. The API supports creating, retrieving, updating, and deleting products. A client interaction script is also provided to interact with the API.

Table of Contents
Features
Setup Instructions
API Endpoints
Testing the API
Client Interaction Script
Features
Endpoints:
Add a new product.
Retrieve all products.
Retrieve a product by ID.
Update a product.
Delete a product.
Error Handling:
400 Bad Request: Invalid input data.
404 Not Found: Requested resource does not exist.
201 Created: Product created successfully.
JSON request and response format.
Setup Instructions
1. Prerequisites
Python 3.7+ must be installed.
Install pip for managing Python packages.
2. Install Required Libraries
Run the following command to install Flask and Requests:

bash
Copy code
pip install flask requests
3. Run the API Server
Save the API code to a file named product_api.py.
Start the API server by running:
python product_api.py
The server will run on http://127.0.0.1:5000.
API Endpoints
1. Retrieve All Products
Endpoint: GET /products
Response: List of all products.
Example:
json
[
    {
        "id": 1,
        "name": "Laptop",
        "description": "A high-performance laptop",
        "price": 1200.99
    }
]
2. Retrieve a Product by ID
Endpoint: GET /products/<product_id>
Response: Product details if found.
Example:
json

{
    "id": 1,
    "name": "Laptop",
    "description": "A high-performance laptop",
    "price": 1200.99
}
3. Add a New Product
Endpoint: POST /products
Request Body (JSON):
json

{
    "name": "Smartphone",
    "description": "A high-end smartphone",
    "price": 799.99
}
Response (201 Created):
json

{
    "id": 2,
    "name": "Smartphone",
    "description": "A high-end smartphone",
    "price": 799.99
}
4. Update a Product
Endpoint: PUT /products/<product_id>
Request Body (JSON):
json

{
    "name": "Updated Laptop",
    "price": 999.99
}
Response:
json

{
    "id": 1,
    "name": "Updated Laptop",
    "description": "A high-performance laptop",
    "price": 999.99
}
5. Delete a Product
Endpoint: DELETE /products/<product_id>
Response:
json

{
    "message": "Product deleted"
}
Testing the API
Manual Testing
Use a tool like Postman or cURL to manually test the API.

Example: Adding a Product with cURL

curl -X POST http://127.0.0.1:5000/products \
-H "Content-Type: application/json" \
-d '{"name": "Laptop", "description": "A high-performance laptop", "price": 1200.99}'
Example: Retrieving All Products with cURL


curl -X GET http://127.0.0.1:5000/products
Client Interaction Script
A Python script is provided to interact with the API.

1. Save the Script
Save the following script to a file named client_script.py:


import requests

BASE_URL = "http://127.0.0.1:5000/products"

def add_product(name, description, price):
    product_data = {"name": name, "description": description, "price": price}
    response = requests.post(BASE_URL, json=product_data)
    if response.status_code == 201:
        print("Product added:", response.json())
    else:
        print("Error:", response.json())

def get_all_products():
    response = requests.get(BASE_URL)
    if response.status_code == 200:
        print("Products:", response.json())
    else:
        print("Error:", response.status_code)

if __name__ == "__main__":
    add_product("Laptop", "A high-performance laptop", 1200.99)
    add_product("Headphones", "Noise-cancelling headphones", 299.99)
    get_all_products()
2. Run the Script
Execute the script to add products and retrieve the list:



python client_script.py
Example Output
plaintext

Adding Products...
Product added: {'id': 1, 'name': 'Laptop', 'description': 'A high-performance laptop', 'price': 1200.99}
Product added: {'id': 2, 'name': 'Headphones', 'description': 'Noise-cancelling headphones', 'price': 299.99}

Retrieving All Products...
Products: [{'id': 1, 'name': 'Laptop', 'description': 'A high-performance laptop', 'price': 1200.99}, {'id': 2, 'name': 'Headphones', 'description': 'Noise-cancelling headphones', 'price': 299.99}]




