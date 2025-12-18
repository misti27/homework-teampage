# 1.main.css

## 1. 全局变量与基础设置（:root 部分）

```css
:root {
    --blue-main: #1a4fa3;       /* 主色调-深蓝色 */
    --blue-light: #e8f0fe;      /* 浅蓝色，用于悬停背景 */
    --bg-page: #f4f7fb;         /* 页面背景色-浅灰蓝 */
    --bg-card: #ffffff;         /* 卡片背景色-纯白 */
    --text-main: #1f2937;       /* 主文字颜色-深灰 */
    --text-muted: #6b7280;      /* 次要文字颜色-中灰 */
    --border-light: #e5e7eb;    /* 边框颜色-浅灰 */
    --text-on-dark: #ffffff;    /* 深色背景上的文字色 */
}
```
## 2. 页面基础布局

```css
body {
    margin: 0;
    font-family: -apple-system, ...;  /* 系统字体栈，优先使用系统字体 */
    background: var(--bg-page);
    color: var(--text-main);
}
```
## 3. 卡片设计系统

```css
.card {
    background: var(--bg-card);
    border-radius: 14px;           /* 较大的圆角，现代感强 */
    padding: 24px;                 /* 统一的内边距 */
    margin-bottom: 28px;           /* 卡片间距 */
    border: 1px solid var(--border-light);
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.04); /* 扩散阴影，提升层次 */
}
```
## 4. 团队成员卡片

```css
.team-members {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    /* 响应式网格：自动适应列数，最小220px */
    gap: 24px; /* 网格间距 */
}

.member-card {
    background-color: aliceblue;  /* 独特背景，与主卡区分 */
    border-radius: 12px;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    /* 同时过渡变换和阴影，动画更丰富 */
}

.member-card:hover {
    transform: translateY(-3px);  /* 悬停上浮效果 */
    box-shadow: 0 6px 16px rgba(0, 0, 0, 0.08);
}
```
## 5. 城市介绍布局系统

```css
.city-row {
    display: flex;
    align-items: center;          /* 垂直居中 */
    gap: 24px;                    /* 图片与文字间距 */
}

.city-row.left-text {
    flex-direction: row;          /* 文字左，图片右 */
}

.city-row.right-text {
    flex-direction: row-reverse;  /* 文字右，图片左 */
}

.city-text-block {
    text-indent: 2em;            /* 首行缩进，中文阅读习惯 */
    text-align: justify;         /* 两端对齐，更整齐 */
    line-height: 1.8;            /* 1.8倍行高，提升可读性 */
}
```
## 6. 导航栏高级设计

```css
.navbar {
    position: sticky;             /* 粘性定位，滚动时保持可见 */
    top: 0;
    z-index: 1000;               /* 确保在最上层 */
}

.nav-item::after {
    content: "";
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    height: 3px;
    background-color: #ffffff;
    opacity: 0;
    transition: opacity 0.2s ease;
}

.nav-item:hover::after {
    opacity: 1;                  /* 悬停时显示底部指示线 */
}
```
## 7. 下拉菜单设计

```css
.dropdown {
    position: relative;           /* 相对定位，作为绝对定位的参考 */
    height: 60px;                /* 与导航栏同高，便于对齐 */
}

.dropdown-menu {
    display: none;               /* 默认隐藏 */
    position: absolute;
    top: 100%;                   /* 在父元素下方 */
    left: 0;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
    border-radius: 0 0 4px 4px;  /* 只圆角底部 */
}

.dropdown:hover .dropdown-menu {
    display: block;              /* 悬停时显示 */
}
```
## 8. 响应式设计系统

```css
@media (max-width: 600px) {
    /* 移动端：卡片内边距减小 */
    .card { padding: 18px; }
    
    /* 移动端：头像尺寸缩小 */
    .member-avatar { 
        width: 72px;
        height: 72px;
    }
    
    /* 移动端：导航垂直排列 */
    .nav-links {
        flex-direction: column !important;
        width: 100%;
    }
    
    /* 移动端：城市介绍垂直排列，图片在上 */
    .city-row {
        flex-direction: column !important;
    }
    .city-image {
        order: -1;              /* 图片显示在文字上方 */
    }
}
```
## 9. 图标与细节处理

```css
.inline-icon {
    width: 30px;
    height: 30px;
    margin-left: 6px;
    vertical-align: text-bottom;  /* 与文字基线对齐 */
}

.city-image img {
    height: 270px;                /* 固定视觉高度 */
    object-fit: cover;            /* 保持比例裁剪 */
}
```