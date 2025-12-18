# Mini SaaS / CRM API

A simple CRM / Mini SaaS backend API built with Django and Django REST Framework.  
Manage customers, products, and orders with a fully RESTful API. Ready for Postman testing.

---

## Features

- CRUD for Customers, Products, and Orders
- Order management with multiple items
- Automated calculation of order totals
- RESTful API ready for Postman testing
- Easy to extend for future SaaS features

---

## Tech Stack

- Python 3.x
- Django
- Django REST Framework
- SQLite (default, can switch to MySQL/PostgreSQL)

---

## Models Overview

1. **Customer**
   - `first_name`, `last_name`, `email`, `phone`, `created_at`
2. **Product**
   - `name`, `description`, `price`, `created_at`
3. **Order**
   - `customer`, `status` (`pending`, `in_progress`, `completed`, `canceled`)
   - `items` (many-to-many with Product via OrderItem)
4. **OrderItem**
   - `product`, `quantity`

---

## API Endpoints

### Customers

| Method | Endpoint             | Description            |
|--------|--------------------|------------------------|
| GET    | `/api/customers/`   | List all customers     |
| POST   | `/api/customers/`   | Create a new customer  |

**Example POST body:**

```json
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john@example.com",
  "phone": "09123456789"
}
```

---

### Products

| Method | Endpoint           | Description           |
|--------|------------------|----------------------|
| GET    | `/api/products/`  | List all products    |
| POST   | `/api/products/`  | Create a new product |

**Example POST body:**

```json
{
  "name": "Product A",
  "description": "Sample product",
  "price": 150.5
}
```

---

### Orders

| Method | Endpoint        | Description                  |
|--------|----------------|------------------------------|
| GET    | `/api/orders/`  | List all orders              |
| POST   | `/api/orders/`  | Create a new order with items|

**Example POST body:**

```json
{
  "customer_id": 1,
  "status": "pending",
  "items": [
    {"product_id": 1, "quantity": 2},
    {"product_id": 2, "quantity": 1}
  ]
}
```

---

## Setup & Run

1. Clone the repository:

```bash
git clone https://github.com/amir-dvlp71/django-mini-crm.git
cd django-mini-crm
```

2. Create virtual environment:

```bash
python -m venv venv
venv\Scripts\activate  # Windows
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Apply migrations:

```bash
python manage.py migrate
```

5. Run server:

```bash
python manage.py runserver
```

6. Test APIs via Postman using the included collection:

```
postman/mini-saas-crm-collection.json
```

---

## Future Improvements

- Add authentication (JWT / Token)
- Async order processing
- Large file support for Orders
- Docker support
- Frontend integration
- Detailed reporting & analytics

---

## Author

Developed by Amir  
Backend Developer | Python & Django
