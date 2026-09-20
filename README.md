# E-Commerce Product API Learning

A Spring Boot REST API for managing e-commerce products, including full CRUD operations, image upload/storage, and keyword search.

## Features
- Create, read, update, and delete products
- Image upload and retrieval (stored as BLOB in database)
- Case-insensitive product search by name, description, brand, or category
- RESTful endpoints with proper HTTP status codes

## Tech Stack
- Java 21
- Spring Boot 3
- Spring Data JPA (Hibernate)
- H2 Database (in-memory, for development)
- Lombok
- Maven

## API Endpoints

| Method | Endpoint                     | Description                  |
|--------|-------------------------------|-------------------------------|
| GET    | /api/products                | Get all products              |
| GET    | /api/product/{id}             | Get a single product by ID    |
| POST   | /api/product                  | Add a new product (with image)|
| PUT    | /api/product/{id}              | Update an existing product    |
| DELETE | /api/product/{id}              | Delete a product               |
| GET    | /api/product/{id}/image        | Get a product's image          |
| GET    | /api/products/search?keyword=  | Search products by keyword     |

## How to Run
1. Clone the repository
2. Open in IntelliJ (or your preferred IDE)
3. Run `EcomProjectLearningApplication.java`
4. API available at `http://localhost:8080/api`
5. H2 console available at `http://localhost:8080/h2-console`

## What I Learned / Challenges Solved
- Debugged a JSON deserialization issue where primitive types (`int`, `boolean`)
  threw exceptions when the frontend sent `null` — fixed by switching to wrapper
  types (`Integer`, `Boolean`).
- Tracked down a bug where a service method (`getProductById`) was returning
  `null` unconditionally, silently breaking both the image endpoint and product
  detail page — fixed by properly implementing the repository lookup.
- Implemented custom search using JPQL with `@Query` and `LIKE` for
  case-insensitive partial matching across multiple fields.