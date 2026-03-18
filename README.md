# SHEIN Shopping Skill

[![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)](./SKILL.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](./LICENSE)

Help users shop smartly on SHEIN with browser automation support.

## Features

### v2.0 - Browser Automation

- 🔍 **Product Search** - Search SHEIN with filters and sorting
- 🔥 **Trend Discovery** - Browse trending styles and new arrivals
- ⚡ **Flash Sales** - Check daily deals and limited-time offers
- 📏 **Size Guide** - View size charts and fit recommendations
- ⭐ **Reviews** - Read user reviews and photo reviews
- 🛒 **Cart Operations** - Add to cart, apply coupons (login required)
- 📋 **Order Preview** - Generate complete order summary (login required)
- 🔒 **User-Controlled Payment** - Agent stops before payment

### Legacy: Decision-Only Mode

- Platform suitability analysis
- Style and trend guidance
- Price-value assessment
- SHEIN vs other platforms comparison

## Installation

```bash
# Via clawhub
clawhub install shein-shopping

# Or clone manually
git clone https://github.com/harrylabsj/shein-shopping.git ~/.openclaw/skills/shein-shopping
```

## Usage

### Shopping Assistance

```
User: "帮我买SHEIN的连衣裙"
Agent: 启动4阶段购物流程
  - Phase 1: 搜索并对比选项
  - Phase 2: 查看详情和评价
  - Phase 3: 加入购物车并生成订单预览（需登录）
  - Phase 4: 用户确认并完成支付
```

### Decision Support

```
User: "SHEIN适合买泳衣吗？"
Agent: 提供平台分析和购买建议
```

## Workflow

### Phase 1: Discovery
- Search products
- Browse trends and flash sales
- Compare top options

### Phase 2: Selection
- View product details
- Check size guide
- Read reviews

### Phase 3: Cart & Pre-Order (Login Required)
- Add to cart
- Apply coupons
- Generate order preview

### Phase 4: Checkout (User-Controlled)
- User reviews order
- User completes payment manually

## Safety

- ✅ Agent stops before payment
- ✅ User retains full purchase control
- ✅ No payment information stored
- ✅ Login requires explicit consent

## Requirements

- OpenClaw with browser automation support
- Chrome browser (for logged-in workflows)
- SHEIN account (for cart operations)

## File Structure

```
shein-shopping/
├── SKILL.md                      # Main skill definition
├── README.md                     # This file
├── package.json                  # Package metadata
├── clawhub.json                  # Clawhub registry config
├── shein-shopping.py             # Python CLI runtime
├── security.py                   # Security utilities
├── requirements.txt              # Python dependencies
└── references/
    ├── fit-guide.md              # Fit and sizing guidance
    ├── output-patterns.md        # Output templates
    └── browser-workflow.md       # Automation guide
```

## CLI Commands

```bash
# Search products
shein-shopping search "dress"

# Login
shein-shopping login

# Price tracking
shein-shopping price <product-url>

# New arrivals
shein-shopping new
```

## References

- [SKILL.md](./SKILL.md) - Complete skill documentation
- [references/browser-workflow.md](./references/browser-workflow.md) - Browser automation guide
- [references/fit-guide.md](./references/fit-guide.md) - Fit and sizing tips
- [references/output-patterns.md](./references/output-patterns.md) - Output templates

## Changelog

### v2.0.0
- Added browser automation support
- 4-phase shopping workflow
- User-controlled payment boundary
- Cart and coupon operations
- Python CLI runtime

### v1.2.0
- Previous stable release

### v1.0.0
- Initial release
- Decision-only mode
- Platform suitability guidance

## License

MIT

## Author

harrylabsj
