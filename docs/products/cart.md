---
title: Shopping cart
description: Collect multiple products before purchasing them together
keywords: [cart, shopping cart, multi-product order]
authors: [hsluoyz]
---

The shopping cart collects products for purchase in a single order. Add items to the cart and complete the transaction when ready instead of buying one at a time.

## Adding products to cart

An **Add to cart** button appears on product pages and in the [Product Store](/docs/products/product-store). Added products are stored in the user's cart and persist across sessions, so users can add items and complete the purchase later.

Regular products are added at their listed price. For recharge products, specify the amount first—either a preset value or a custom amount. The system validates that custom amounts are greater than zero before adding.

Subscription products can also be added to the cart. Each subscription is treated as a separate line item; the cart handles the order and payment flow for both regular and subscription products.

## Currency consistency

All items in the cart must use the same currency. Adding a product in a different currency than existing items is blocked, and the system reports the mismatch. This keeps the order total accurate at checkout.

## Managing the cart

Open the cart via **Cart** in the Business & Payments section. The cart page shows:

- Product name and display name
- Product image
- Price and currency
- Quantity (managed automatically)

Each item has a **Buy** button to purchase that product alone or a **Delete** button to remove it. Quantities are tracked automatically—adding the same product at the same price increases the quantity instead of creating duplicate rows.

To remove all items at once, click **Clear** at the top of the cart. A confirmation prompt is shown before the cart is emptied.

## Placing orders from cart

Click **Buy** next to any item to purchase it individually. Use the **Place Order** button at the top of the cart to initiate payment for all items at once—each item is processed as a separate order.

After purchasing, remove items from the cart manually or leave them for reference.
