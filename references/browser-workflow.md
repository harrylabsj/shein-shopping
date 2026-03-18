# SHEIN Browser Automation Workflow

## Overview

This guide documents the browser automation workflow for SHEIN shopping assistance.

## Supported Operations

### Phase 1: Discovery (No Login Required)

#### Search Products
```
URL: https://www.shein.com/search?q={keyword}
Actions:
  - Enter search term
  - Apply filters (category, price, rating)
  - Sort results (recommended, price, newest)
Output:
  - Product list with prices, ratings
  - Available filters applied
```

#### Browse Trends/New Arrivals
```
URL: https://www.shein.com/new-products.html
Actions:
  - Navigate to new arrivals
  - Browse trending categories
  - Check daily deals section
Output:
  - Trending items
  - Flash sale items
```

#### Check Flash Sales
```
URL: https://www.shein.com/campaigns
Actions:
  - View active flash sales
  - Check sale countdown timers
  - Browse sale categories
Output:
  - Current promotions
  - Time-limited deals
```

### Phase 2: Selection (No Login Required)

#### View Product Detail
```
URL: https://www.shein.com/product-{id}.html
Actions:
  - Open product page
  - Extract product details
  - View size chart
  - Read reviews
Output:
  - Product title, description
  - Original price, current price
  - Available sizes/colors
  - Material information
  - User rating, review count
  - Size chart data
```

#### Check Reviews
```
Actions:
  - Scroll to reviews section
  - Read user reviews
  - View photo reviews if available
Output:
  - Review summary
  - Common feedback themes
  - Photo review availability
```

### Phase 3: Cart Operations (Login Required)

#### Add to Cart
```
Prerequisites:
  - User must be logged in
  - Product size/color selected
Actions:
  - Select size/color
  - Click "Add to Bag"
  - Confirm addition
Output:
  - Cart update confirmation
  - Current cart item count
```

#### View Cart
```
URL: https://www.shein.com/shoppingbag.html
Actions:
  - Navigate to shopping bag
  - Review cart contents
Output:
  - Item list with quantities
  - Individual prices
  - Subtotal
```

#### Apply Coupons
```
Actions:
  - Check available promo codes
  - Apply applicable coupons
  - Calculate discounts
Output:
  - Applied discounts
  - Updated total
```

#### Generate Order Preview
```
Actions:
  - Proceed to checkout preview
  - Select/confirm address
  - Calculate shipping
  - Apply all discounts
Output:
  - Complete order summary
  - Item details
  - Discounts applied
  - Shipping cost
  - Final total
```

## Login Handling

### Option A: Chrome Profile with Active Session
```
1. Navigate to shein.com
2. Check for login state
3. If logged in: proceed with cart operations
4. If not logged in: prompt user
```

### Option B: Manual Mode (No Login)
```
1. Provide search results
2. Give product recommendations
3. Provide step-by-step manual instructions
4. User completes purchase independently
```

## Safety Boundaries

### Agent CAN:
- Search and browse products
- Compare prices and options
- Check reviews and ratings
- Add items to cart (with login)
- Apply coupons (with login)
- Generate order previews (with login)

### Agent CANNOT:
- Complete payment
- Submit final orders
- Store payment information
- Store login credentials
- Make purchases without user confirmation

## Error Handling

### CAPTCHA
```
When encountered:
  - Stop automation
  - Notify user
  - Provide manual instructions
```

### Out of Stock
```
When encountered:
  - Notify user
  - Suggest alternatives
  - Check back-in-stock options
```

### Login Required
```
When encountered:
  - Ask user for consent
  - Provide manual alternative
  - Do not proceed without permission
```

## Data Points to Capture

### Product Information
- Title
- Original price
- Current price
- Discount percentage
- Available sizes
- Available colors
- Material
- Rating
- Review count

### Cart Information
- Items
- Quantities
- Individual prices
- Subtotal
- Applied discounts
- Shipping cost
- Final total

### Order Preview
- Delivery address
- Items with details
- Price breakdown
- Payment methods available (for info only)
