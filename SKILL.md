# SHEIN-EC (希音电商) Skill

CLI tool for SHEIN fashion e-commerce platform, now aligned with the shared browser-commerce workflow for live product, price, stock, and account-page checks.

## Browser Workflow Upgrade

When the task involves live SHEIN pages, follow the shared **browser-commerce-base** workflow:
- public search/detail/new-arrival pages → `openclaw`
- login/account/order/coupon pages → `user` only when needed
- re-snapshot after size/color/filter changes because fashion pages refresh price and stock often
- capture stock hints, sale framing, and final price in screenshots

Key browser extraction order on SHEIN:
- 商品标题
- 当前价 / 折后价
- 尺码 / 颜色 / 库存提示
- 活动标签 / 限时折扣
- 发货或预计送达提示
- 风险提示（断码、库存紧张、价格波动）

## Commands

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

## Features

- Product search with caching
- QR code login
- Price history tracking
- New arrivals query
- Anti-detection browser automation

## Dependencies

- Python 3.9+
- `playwright>=1.40.0` (浏览器自动化)
- `cryptography>=42.0.0` (加密库)
- 安装命令: `pip install -r requirements.txt`

## 数据存储与安全

### 存储位置
- **主目录**: `~/.openclaw/data/shein-shopping/secure/` (加密存储)
- **会话数据**: `cookies.enc` (AES-256 加密存储)
- **缓存数据**: `shein-shopping.db` (SQLite数据库)
- **加密密钥**: `.key` (权限 600)

### 隐私保护
1. **加密存储**: 所有敏感数据使用 Fernet 加密
2. **用户同意**: 首次运行需要明确同意数据使用条款
3. **数据控制**: 支持一键清除所有个人数据
4. **透明审计**: 可查看所有存储的文件和权限

### 隐私控制命令
```bash
# 查看隐私信息
shein-shopping privacy info

# 清除所有个人数据
shein-shopping privacy clear

# 导出加密数据（备份）
shein-shopping privacy export
```

## Security
This skill uses browser automation for legitimate shopping assistance only.
All user data is encrypted and stored locally. No data transmission to external servers.
See SECURITY.md for details.
