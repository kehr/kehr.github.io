# Kaixuan AI 个人作品集网站项目

## 项目概述

这是一个基于 Astro 框架构建的现代化个人作品集网站，专为 AI 产品设计师/开发者量身定制。网站采用响应式设计，支持深色/浅色主题切换，展示个人项目、技能和专业背景。

### 核心信息
- **项目名称**: dimensional-disk (Kaixuan AI Portfolio)
- **域名**: http://kaixuan.ai
- **GitHub**: https://github.com/kehr
- **博客**: https://blog.kaixuan.ai
- **技术栈**: Astro 5.13.2 + TypeScript + CSS Variables
- **部署**: GitHub Pages (推测)

## 技术架构

### 框架与工具
- **前端框架**: Astro 5.13.2 (Static Site Generator)
- **语言**: TypeScript + HTML + CSS
- **样式方案**: 原生 CSS + CSS Variables (无外部框架)
- **构建工具**: Astro CLI
- **包管理**: npm

### 项目结构详解

```
kehr.github.io/
├── .cursor/                    # Cursor IDE 配置目录
│   └── PROJECT.md             # 项目说明文档
├── public/                    # 静态资源目录
│   ├── assets/               # 图片资源
│   │   ├── backgrounds/      # 背景图片(支持响应式和主题)
│   │   └── stock-*.jpg      # 项目展示图片
│   └── favicon.svg          # 网站图标
├── src/                      # 源代码目录
│   ├── components/          # Astro 组件
│   ├── content/            # 内容管理
│   │   └── work/          # 作品集内容(Markdown)
│   ├── layouts/           # 页面布局
│   ├── pages/            # 页面路由
│   └── styles/          # 全局样式
├── astro.config.mjs        # Astro 配置
├── package.json           # 项目依赖
├── tsconfig.json         # TypeScript 配置
└── README.md            # 项目说明
```

## 功能模块分析

### 1. 页面结构
- **首页 (`/`)**: 展示个人介绍、核心技能、精选作品和媒体提及
- **作品页 (`/work/`)**: 完整作品集展示，支持动态路由
- **关于页 (`/about/`)**: 个人背景、教育经历、技能详情
- **个人作品详情页 (`/work/[...slug]/`)**: 动态路由展示具体项目

### 2. 核心组件

#### 布局组件
- `BaseLayout.astro`: 基础页面布局，包含导航、页脚和主题系统
- `MainHead.astro`: HTML头部管理，SEO优化

#### UI 组件
- `Hero.astro`: 主标题区域，支持居中/左对齐
- `Nav.astro`: 响应式导航栏，支持移动端菜单
- `Footer.astro`: 页脚组件
- `Skills.astro`: 技能展示卡片
- `PortfolioPreview.astro`: 作品预览卡片
- `Grid.astro`: 响应式网格布局
- `Icon.astro`: SVG 图标系统
- `ThemeToggle.astro`: 主题切换器

#### 功能组件
- `ContactCTA.astro`: 联系行动召唤
- `CallToAction.astro`: 通用行动召唤按钮
- `Pill.astro`: 标签样式组件

### 3. 内容管理系统

#### 内容配置 (`content.config.ts`)
- 使用 Astro Content Collections
- 支持 Markdown 文件管理
- 类型安全的内容架构验证

#### 作品集数据结构
```typescript
{
  title: string;           // 项目标题
  description: string;     // 项目描述
  publishDate: Date;       // 发布日期
  tags: string[];         // 技术标签
  img: string;            // 预览图片
  img_alt?: string;       // 图片描述
}
```

#### 现有作品案例
1. **Bloom Box** (2019-12-01)
   - AI 音乐播放列表 + 植物健康优化
   - 标签: Dev, Branding, Backend

2. **h2.0** (2019-10-02)
   - 彩色水产品品牌设计
   - 标签: Design, Branding

3. **Duvet Genius** (2020-03-04)
   - 虚拟床品展示平台
   - 标签: Design, Dev, Branding

4. **Markdown Mystery Tour** (日期待定)
   - Markdown 相关项目

### 4. 设计系统

#### 主题支持
- **浅色主题**: 白色背景 + 深色文字
- **深色主题**: 深色背景 + 浅色文字
- 通过 CSS 变量实现主题切换
- 支持用户偏好检测

#### 色彩系统
```css
/* 主色调 */
--accent-light: #c561f6;    /* 浅紫色 */
--accent-regular: #7611a6;  /* 主紫色 */
--accent-dark: #1c0056;     /* 深紫色 */

/* 灰度系统 */
--gray-0 到 --gray-999      /* 完整灰度阶梯 */
```

#### 响应式设计
- 移动优先的设计理念
- 50em (800px) 断点进行桌面端优化
- 灵活的网格系统和间距系统

#### 背景系统
- 支持多层背景合成
- 响应式图片加载 (800w/1440w)
- 噪点纹理叠加效果
- 主题相关的背景切换

### 5. 性能优化

#### 图片优化
- 响应式图片支持 (800w, 1440w)
- 懒加载背景图片
- WebP 格式支持 (推测)

#### 加载策略
- 关键背景图片优先加载
- 非关键背景图片延迟加载 (.loaded 类触发)
- 最小化 JavaScript 使用

## 开发指南

### 本地开发环境

```bash
# 安装依赖
npm install

# 启动开发服务器
npm run dev          # http://localhost:4321

# 构建生产版本
npm run build

# 预览构建结果
npm run preview

# Astro CLI 命令
npm run astro -- --help
```

### 内容管理

#### 添加新项目
1. 在 `src/content/work/` 目录创建新的 Markdown 文件
2. 按照规定格式填写 frontmatter
3. 添加项目详情内容
4. 放置项目图片到 `public/assets/`

#### 修改个人信息
- **导航栏**: 修改 `src/components/Nav.astro`
- **首页介绍**: 修改 `src/pages/index.astro`
- **关于页面**: 修改 `src/pages/about.astro`
- **技能展示**: 修改 `src/components/Skills.astro`

### 样式定制

#### 修改主题色彩
在 `src/styles/global.css` 中修改 CSS 变量:
```css
:root {
  --accent-regular: #your-color;
  /* 其他颜色变量 */
}
```

#### 添加新字体
在 `global.css` 中修改字体变量:
```css
--font-body: "Your-Font", var(--font-system);
--font-brand: "Your-Brand-Font", var(--font-system);
```

## 部署配置

### GitHub Pages 部署
项目配置为部署到 GitHub Pages:
- **站点配置**: `http://kaixuan.ai` (自定义域名)
- **CNAME 文件**: 已配置自定义域名
- **构建命令**: `npm run build`
- **输出目录**: `./dist/`

### 环境变量
```javascript
// astro.config.mjs
export default defineConfig({
    site: 'http://kaixuan.ai'  // 生产环境 URL
});
```

## 维护指南

### 定期维护任务
1. **依赖更新**: 定期更新 Astro 和相关依赖
2. **内容更新**: 添加新项目和更新个人信息
3. **性能监控**: 检查加载性能和 Core Web Vitals
4. **SEO 优化**: 更新元数据和结构化数据

### 常见问题排查

#### 图片不显示
- 检查图片路径是否正确 (相对于 `public/` 目录)
- 确认图片文件存在且命名正确

#### 主题切换异常
- 检查 `ThemeToggle.astro` 组件
- 确认 CSS 变量定义完整

#### 内容不显示
- 验证 Markdown frontmatter 格式
- 检查 `content.config.ts` 架构定义

## 扩展建议

### 功能扩展
1. **博客系统**: 集成博客功能到主站
2. **搜索功能**: 添加项目搜索和过滤
3. **国际化**: 支持多语言切换
4. **动画效果**: 添加页面过渡和交互动画
5. **联系表单**: 集成联系表单功能

### 技术升级
1. **图片优化**: 集成 Astro Image 组件
2. **PWA 支持**: 添加离线功能
3. **分析工具**: 集成 Google Analytics
4. **CMS 集成**: 考虑 Headless CMS 方案

## 注意事项

### 开发注意事项
- Astro 使用服务端渲染，注意客户端 JavaScript 的使用
- 图片资源放在 `public/` 目录，引用时不需要 `/public` 前缀
- CSS 变量实现主题切换，避免使用内联样式
- 保持组件的单一职责原则

### 性能考虑
- 优化图片大小和格式
- 最小化 CSS 和 JavaScript bundle
- 利用 Astro 的部分水化特性
- 合理使用浏览器缓存

### 可访问性
- 确保充足的颜色对比度
- 提供替代文本和语义化标签
- 支持键盘导航
- 兼容屏幕阅读器

---

**最后更新**: 2024年12月 | **维护者**: Kaixuan AI | **版本**: v0.0.1
