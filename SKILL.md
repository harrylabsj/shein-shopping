---
name: shein-shopping
version: 2.0.0
description: Shop SHEIN with browser automation for trend search, style discovery, price comparison, cart operations, and deal tracking. Supports logged-in workflows for browsing, adding to cart, checking flash sale prices, and order preview while keeping checkout/payment for user control. Use when the user wants to buy affordable fashion, explore trends, or compare value on SHEIN.
---

# SHEIN Shopping

Help users shop smartly on SHEIN, the global fast-fashion platform known for trendy styles, affordable prices, and frequent flash sales.

## Capabilities

### v2.0 - Browser Automation Support

| Operation | Auth Required | Description |
|-----------|---------------|-------------|
| **Search** | Optional | Search products, filter by category/price/style |
| **Trend Discovery** | Optional | Browse trending styles, new arrivals, flash sales |
| **Product Detail** | Optional | View specs, prices, size charts, reviews |
| **Price Comparison** | Optional | Compare prices across similar items |
| **Size Guide Check** | Optional | View size charts and fit recommendations |
| **Reviews** | Optional | Read user reviews, ratings, photos |
| **Add to Cart** | ✅ Required | Add items to shopping cart |
| **View Cart** | ✅ Required | Review cart contents |
| **Apply Coupons** | ✅ Required | Check and apply promo codes, flash sale discounts |
| **Generate Order Preview** | ✅ Required | Calculate final price with all discounts |
| **Payment** | ❌ Blocked | User must complete payment manually |

**Safety Rule**: Agent stops before payment. User retains full control over final purchase.

### Legacy: Decision-Only Mode (No Browser)

- Platform suitability analysis
- Style and trend guidance
- Price-value assessment
- Fit and quality expectations
- SHEIN vs other platforms comparison

Read these references as needed:
- `references/fit-guide.md` for fit and sizing guidance
- `references/output-patterns.md` for output patterns
- `references/browser-workflow.md` for automation guide

## Workflow

### Phase 1: Discovery (Agent-Assisted)
1. **Search** - Agent searches SHEIN for target products
2. **Trend Browse** - Explore trending styles, new arrivals
3. **Flash Sales** - Check 限时特惠, daily deals
4. **Filter & Sort** - Apply filters (category, price range, rating)
5. **Compare** - Agent compares top options

### Phase 2: Selection (Agent-Assisted)
1. **Product Detail** - Agent opens selected product page
2. **Price Analysis** - Compare current price vs original price
3. **Size Guide** - Check size chart and fit recommendations
4. **Reviews Check** - Read user reviews and photo reviews
5. **Quality Assessment** - Review material description and ratings

### Phase 3: Cart & Pre-Order (Agent-Assisted with Login)
1. **Add to Cart** - Agent adds item to cart (requires login)
2. **Cart Review** - Agent shows cart contents, quantities
3. **Coupon Application** - Agent checks promo codes, flash sale discounts
4. **Address Selection** - Agent confirms delivery address
5. **Order Summary** - Agent generates complete order preview

### Phase 4: Checkout (User-Controlled)
1. **Handoff** - Agent presents final order details
2. **User Review** - User confirms all details are correct
3. **Payment** - ⚠️ **User completes payment manually**
4. **Confirmation** - User shares order confirmation if desired

**Agent Boundary**: Stops at Phase 3. Never executes payment or final order submission.

### Legacy: Decision-Only Mode (No Browser)

1. Identify the user's shopping need
2. Focus on public decision-relevant factors
3. Explain trade-offs
4. Give practical next-step advice

## Output

### For Shopping Assistance (v2.0)

#### Product Comparison
| # | 商品 | 原价 | 现价 | 折扣 | 评分 | 库存状态 |
|---|------|------|------|------|------|---------|
| 1 | ... | ... | ... | ... | ... | ✅ 有货 |

#### Selected Product
- **名称**: 
- **原价 / 现价**: 
- **折扣**: 
- **材质**: 
- **尺码建议**: 
- **评分**: 
- **优惠券**: 

#### Cart Summary (if applicable)
- 商品小计: 
- 优惠券抵扣: 
- 运费: 
- **应付总额**: 

#### Next Steps
1. [Agent completed] ...
2. [User action] 打开 SHEIN App/网站 完成支付

### For Decision-Only Mode (Legacy)

#### Best Option
State the strongest current choice.

#### Why
List the main reasons.

#### Caveats
List meaningful concerns or trade-offs.

#### Final Advice
Give a direct practical buying suggestion.

## Agent Execution Guide

### When User Says "帮我买..." / "帮我下单..."

```
User: "帮我买SHEIN的衣服"
  ↓
Step 1: Confirm Intent
  "我来帮你搜索SHEIN的衣服，查看流行趋势，对比价格，加入购物车。
   最后需要你确认订单并完成支付。可以吗？"
  ↓
Step 2: Discovery Phase (No login required)
  - Search SHEIN for "衣服"
  - Browse trending styles, new arrivals
  - Check flash sales and daily deals
  - Filter by category, price range
  - Compare top 3 options
  ↓
Step 3: Selection Phase (No login required)
  - User picks one option
  - Agent opens product page
  - Check size guide and fit recommendations
  - Read user reviews and photos
  - Confirm material and quality indicators
  ↓
Step 4: Cart Phase (⚠️ Requires login)
  "接下来需要登录你的SHEIN账号才能加入购物车，
   请确认是否继续？"
  - If yes: proceed with browser automation
  - If no: provide manual instructions
  ↓
Step 5: Order Generation (Requires login)
  - Add to cart
  - Apply promo codes, flash sale discounts
  - Select address
  - Calculate final price (including shipping)
  - Generate order preview
  ↓
Step 6: Handoff (User-controlled)
  "订单已准备好，请检查：
   [订单详情摘要]
   
   👉 请手动完成支付：
   1. 打开 SHEIN App 或网站
   2. 进入购物车
   3. 点击结算
   4. 确认地址和优惠券
   5. 提交订单并支付"
```

### Browser Automation Rules

**Always announce before action:**
- "正在搜索..."
- "正在查看流行趋势..."
- "正在检查尺码指南..."
- "正在加入购物车..."

**Snapshot key information:**
- Product title, original price, current price
- Discount percentage
- Size availability and size chart
- Material description
- User rating and review count
- Photo reviews
- Available promo codes
- Shipping cost estimate

**Stop conditions:**
- Before any payment screen
- When CAPTCHA appears (hand to user)
- When login is required (ask first)
- When desired size/color out of stock

### Login Handling

**Option A: User already logged in (Chrome profile)**
```
browser navigates to SHEIN
If user profile has active session → proceed
If session expired → prompt user to login manually first
```

**Option B: Manual mode (no login)**
```
Agent provides:
- Exact search keywords
- Trend and style recommendations
- Size guide tips
- Step-by-step manual instructions
User executes manually
```

## CLI Commands (Python Runtime)

### Search Products
```bash
shein-shopping search "dress"
shein-shopping search "shoes" --page 2 --limit 20
```

### Login
```bash
shein-shopping login
```
Opens browser with QR code for authentication.

### Price Tracking
```bash
shein-shopping price <product-url>
```
Shows current price and historical data.

### New Arrivals
```bash
shein-shopping new
shein-shopping new women
shein-shopping new men
```
Query new arrivals by category.

## Data Storage & Security

### Storage Location
- **Main directory**: `~/.openclaw/data/shein-shopping/secure/` (encrypted)
- **Session data**: `cookies.enc` (AES-256 encrypted)
- **Cache data**: `shein-shopping.db` (SQLite database)
- **Encryption key**: `.key` (permission 600)

### Privacy Controls
```bash
# View privacy info
shein-shopping privacy info

# Clear all personal data
shein-shopping privacy clear

# Export encrypted data (backup)
shein-shopping privacy export
```

## SHEIN Shopping Tips

### When SHEIN is a Good Fit

| Scenario | Why SHEIN Works |
|----------|-----------------|
| **Trend experimentation** | Low cost to try new styles |
| **Occasion shopping** | One-time event outfits |
| **Budget constraints** | Very affordable prices |
| **Fast refresh** | Frequent wardrobe updates |
| **Style exploration** | Wide variety to discover preferences |

### Flash Sales & Deals

| Sale Type | Timing | Best For |
|-----------|--------|----------|
| **限时特惠** | Daily rotating | Deep discounts on select items |
| **New User Deals** | First purchase | Extra discounts for new accounts |
| **Seasonal Sales** | Holiday periods | Site-wide promotions |
| **App-Exclusive** | Mobile only | Additional app-only discounts |

### Quality Considerations

| Factor | Notes |
|--------|-------|
| **Material** | Check description carefully; often synthetic blends |
| **Sizing** | Runs small; size up recommended; check size chart |
| **Quality variance** | Inconsistent; reviews are essential |
| **Return policy** | Free returns within 30 days (check current policy) |
| **Shipping time** | 1-2 weeks standard; express available |

## Quality Bar

### Do:
- ✅ Focus on trend variety and value pricing
- ✅ Check reviews and photos before recommending
- ✅ Verify size availability using size charts
- ✅ Use browser automation for search/cart
- ✅ Add to cart and apply coupons (with consent)
- ✅ Generate order preview with all discounts
- ✅ Stay honest about not doing payment operations

### Do not:
- ❌ Pretend to log in (ask first)
- ❌ Recommend items with poor reviews or no stock
- ❌ Store user data persistently without encryption
- ❌ **Execute payment or final order submission**
- ❌ Guarantee fit or quality without checking reviews

## References

Read these references as needed:
- `references/fit-guide.md` for fit and sizing guidance
- `references/output-patterns.md` for output patterns
- `references/browser-workflow.md` for automation guide