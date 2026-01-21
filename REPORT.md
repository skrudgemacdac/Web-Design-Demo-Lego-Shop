Lego shop Demo Project.

What the website does

- Browse a product catalog
- Use search and filters (age, price range, series/category, piece count)
- Open a product details page
- Add items to cart and proceed to checkout
- Add/remove items from a wishlist
- Open informational pages: About, Contacts, Registration

What was changed on the frontend

- Unified fallback products so that the same demo products are used in both the catalog and the product details page
  - Shared list lives in `frontend/src/data/fallbackProducts.js`
- Product images: fallback products use internet image URLs, and the UI supports both:
  - `imageUrl` (backend/local path or full URL)
  - `img` (full URL used by fallback products)
- Currency display switched to USD in product cards and product detail view, and filter labels were updated accordingly

Backend database schema

The SQL schema is defined in:

- `backend/src/main/resources/createTable.sql`

It creates the tables needed to support the frontend features.

Entities (tables)

- `users`
- `products`
- `wishlist_items`
- `cart_items`
- `orders`
- `order_items`

Relationships

- User → WishlistItem: users (1) -> (many) wishlist_items
  - wishlist_items.user_id → users.id
- Product → WishlistItem: products (1) -> (many) wishlist_items
  - wishlist_items.product_id → products.id
- User → CartItem: users (1) -> (many) cart_items
  - cart_items.user_id → users.id
- Product → CartItem: products (1) -> (many) cart_items
  - cart_items.product_id → products.id
- User → Order: users (1) -> (many) orders(nullable for guest orders)
  - orders.user_id → users.id
- Order → OrderItem: orders (1) -> (many) order_items
  - order_items.order_id → orders.id
- Product → OrderItem: products (1) -> (many) order_items (nullable if product is deleted)
  - order_items.product_id → products.id

Adam Muzaev                 
Student ID:23040102080
GitHub: https://github.com/skrudgemacdac/Web-Design-Demo-Lego-Shop.git



