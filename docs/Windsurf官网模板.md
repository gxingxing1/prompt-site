```markdown
# Windsurf Editor Website

基于 Magic UI 和现代前端技术栈构建的专业代码编辑器官网。


# 前端技术栈
```
核心框架：
- Next.js
- React
- TypeScript

样式解决方案：
- TailwindCSS
- Magic UI（主要UI组件）
- shadcn/ui（补充组件）
- radix-ui（基础组件）

动画与主题：
- Framer Motion
- next-themes

状态管理：
- Redux Toolkit / Zustand
```


# Magic UI 项目搭建完整指南

## 1. 创建项目

```bash
# 使用 create-next-app 创建项目
npx create-next-app@latest magic-site --typescript --tailwind --eslint

# 进入项目目录
cd magic-site
```

## 2. 安装核心依赖

```bash
# 安装基础依赖
npm install tailwindcss-animate class-variance-authority clsx tailwind-merge @radix-ui/react-dropdown-menu @radix-ui/react-icons @radix-ui/react-navigation-menu framer-motion next-themes zustand @shadcn/ui lucide-react --legacy-peer-deps
```

## 3. 初始化 shadcn/ui

```bash
# 运行初始化命令
npx shadcn@latest init

# 选择配置:
# Style: New York
# Base color: Zinc
# CSS variables: Yes
```

## 4. 项目结构
```
src/
├── app/
│   ├── layout.tsx
│   └── page.tsx
├── components/
│   ├── ui/           # Magic UI & shadcn/ui 组件
│   └── sections/     # 页面区块组件
├── lib/
│   └── utils.ts      # 工具函数
└── styles/
    └── globals.css   # 全局样式
```


# Magic UI 组件安装与使用指南

## 1. 核心动效组件安装

```bash
npx shadcn@latest add "https://magicui.design/r/sparkles-text"
npx shadcn@latest add "https://magicui.design/r/animated-gradient-text"
npx shadcn@latest add "https://magicui.design/r/box-reveal"
npx shadcn@latest add "https://magicui.design/r/shimmer-button"
npx shadcn@latest add "https://magicui.design/r/rainbow-button"
npx shadcn@latest add "https://magicui.design/r/magic-card"
npx shadcn@latest add "https://magicui.design/r/border-beam"
npx shadcn@latest add "https://magicui.design/r/marquee"
npx shadcn@latest add "https://magicui.design/r/animated-beam"
```

## 2. 使用示例

### 文字动效

```tsx
// SparklesText 示例
import { SparklesText } from "@/components/ui/sparkles-text"

export default function Demo() {
  return (
    <SparklesText 
      text="Magic UI"
      sparklesCount={20}
      colors={{first: '#A07CFE', second: '#FE8FB5'}}
    />
  )
}

// AnimatedGradientText 示例
import { AnimatedGradientText } from "@/components/ui/animated-gradient-text"

export default function Demo() {
  return (
    <AnimatedGradientText>
      Introducing Magic UI
    </AnimatedGradientText>
  )
}
```

### 按钮动效

```tsx
// ShimmerButton 示例
import { ShimmerButton } from "@/components/ui/shimmer-button"

export default function Demo() {
  return (
    <ShimmerButton 
      shimmerColor="#ffffff"
      shimmerSize="0.1em"
      shimmerDuration="2s"
    >
      Get Started
    </ShimmerButton>
  )
}

// RainbowButton 示例
import { RainbowButton } from "@/components/ui/rainbow-button"

export default function Demo() {
  return (
    <RainbowButton className="px-8 py-2">
      Get Unlimited Access
    </RainbowButton>
  )
}
```

### 卡片动效

```tsx
// MagicCard 示例
import { MagicCard } from "@/components/ui/magic-card"

export default function Demo() {
  return (
    <MagicCard 
      gradientSize={200}
      gradientColor="#262626"
      gradientTransparency={80}
    >
      <div className="p-4">
        <h3>Magic Card</h3>
        <p>Hover me to see the effect</p>
      </div>
    </MagicCard>
  )
}

// BorderBeam 示例
import { BorderBeam } from "@/components/ui/border-beam"

export default function Demo() {
  return (
    <div className="relative h-[200px] w-[200px] rounded-xl">
      <BorderBeam 
        size={300}
        duration={15}
        colorFrom="#ffaa40"
        colorTo="#9c40ff"
      />
      <div className="p-4">Content here</div>
    </div>
  )
}
```

## 3. 注意事项

1. Magic UI 是基于 shadcn/ui 构建的,需要先配置好 shadcn/ui 环境
2. 每个组件都需要单独安装
3. 所有组件都支持自定义样式(通过 className 属性)
4. 动效组件大多支持自定义动画参数


# 页面结构与组件设计

## 首页

### 1. 导航栏 (Navbar)

- **Logo 区域**: `<Link />`
  - Codeium logo (SVG)
  - 点击跳转到首页
  - 悬停时添加轻微缩放效果

- **主导航菜单**: `<NavigationMenu />`
  - 下拉菜单项:
    - Products ▾
    - Capabilities ▾
    - Engines ▾
  - 常规菜单项:
    - Pricing
    - Enterprise
    - Resources ▾
    - Company ▾

- **右侧功能区**:
  - 主题切换: `<ThemeToggle />`
    - 圆形按钮设计
    - 使用 "S" 作为图标
  - 下载按钮: `<ShimmerButton />` 
    - 文字: "Download"
    - 使用品牌主色 (#00FFB9)
    - 添加光效动画

### 实现细节

1. **布局设计**
   - 使用 Flex 布局
   - Logo 靠左对齐
   - 导航菜单居中
   - 功能区靠右对齐
   - 固定在页面顶部

2. **交互效果**
   - 下拉菜单平滑展开
   - 菜单项悬停时显示下划线
   - 按钮悬停时添加光效
   - 滚动时导航栏背景模糊效果

3. **响应式设计**
   - 在移动设备上转为汉堡菜单
   - 保持 Logo 和下载按钮可见
   - 折叠菜单项到抽屉导航

4. **视觉效果**
   - 半透明背景
   - 细微的边框分隔
   - 导航项间距保持一致

### 2. 首页 Hero 区域

- **顶部文本**: `<SparklesText />` (Magic UI)
  - 文字: "From the creators of Codeium, the best AI-powered code extension"
  - 使用较小字号，带有微妙的闪光效果

- **主标题**: `<AnimatedGradientText />` (Magic UI)
  - 文字: "Introducing the Windsurf Editor"
  - 使用大号字体 (64px+)
  - 渐变动画效果：从左到右流动
  - 字体选用: Inter 或类似现代无衬线字体

- **副标题**: `<SparklesText />` (Magic UI)
  - 文字: "The new purpose-built IDE to harness magic"
  - 使用中等字号
  - 带有轻微的发光效果

- **按钮组**: 
  - "Explore Windsurf": `<ShimmerButton />` (Magic UI)
    - 使用品牌主色 (#00FFB9)
    - 添加光效动画
  - "Codeium Extensions": `<Button />` (shadcn/ui)
    - 使用暗色背景
    - 悬停时显示边框效果

### 实现细节

1. **布局设计**
   - 垂直居中布局
   - 文本居中对齐
   - 元素间距保持黄金比例

2. **动画效果**
   - 标题文字使用渐变流动动画
   - 按钮添加悬停和点击反馈
   - 整体区域使用淡入动画

3. **响应式设计**
   - 在移动设备上调整字体大小
   - 按钮在小屏幕上垂直排列

4. **背景设计**
   - 深色背景
   - 添加细微的网格线效果
   - 四角使用装饰性点缀

### 3. 编辑器展示区

- **容器**: `<BorderBeam />` (Magic UI)

  - 使用 Border Beam 为图片容器添加动态边框效果
  - 图片地址：https://exafunction.github.io/public/images/windsurf/windsurf-ide.png

- **功能演示视频**
  - 视频链接：
    - Autocomplete: [https://exafunction.github.io/public/demos/autocompleteAnimation.webp](https://exafunction.github.io/public/demos/autocompleteAnimation.webp)
    - Chat: [https://exafunction.github.io/public/demos/chatAnimation.webp](https://exafunction.github.io/public/demos/chatAnimation.webp)
    - Command: [https://exafunction.github.io/public/demos/commandAnimation.webp](https://exafunction.github.io/public/demos/commandAnimation.webp)
    - Supercomplete: [https://exafunction.github.io/public/demos/superCompleteAnimation.webp](https://exafunction.github.io/public/demos/superCompleteAnimation.webp)

### 实现细节

1. **Border Beam 设置**

   - 动态边框颜色从 `#ffaa40` 到 `#9c40ff`
   - 动画持续时间设置为 15 秒

2. **视频切换效果**

   - 使用淡入淡出动画切换视频
   - 确保视频在切换时流畅播放

3. **交互体验**

   - 按钮点击时有轻微的缩放反馈
   - 鼠标悬停时显示微妙的动画效果

4. **响应式设计**
   - 在移动端将横向布局改为纵向
   - 视频容器保持合适的宽高比

### 4. 企业展示区

- **标题**: `<SparklesText />` (Magic UI)

  - 文字内容: "Codeium lets the world's leading enterprises dream bigger"
  - 居中显示，带有闪光效果

- **企业 Logo 展示**: `<BoxReveal />` (Magic UI)

  - 使用两行网格布局展示企业 Logo
  - 所有 Logo 使用 SVG 格式，保持单色（白色）显示

- **Logo 列表**:
  第一行:

  - Anduril (svg)
  - JPMorgan Chase (svg)
  - Vector (svg)
  - Dell (svg)

  第二行:

  - World Wide Technology (svg)
  - Clearwater Analytics (svg)
  - Zillow (svg)

### 实现细节

1. **布局设计**

   - 使用 CSS Grid 创建两行布局
   - Logo 间距保持一致
   - 确保所有 Logo 大小协调

2. **动画效果**

   - 使用 BoxReveal 实现滚动时的渐入效果
   - Logo 悬停时添加轻微的缩放效果

3. **响应式设计**

   - 在较小屏幕上调整为单列布局
   - 保持 Logo 的清晰度和可读性

4. **可访问性**
   - 为每个 Logo 添加适当的 alt 文本
   - 确保适当的颜色对比度

### 5. 产品对比区

- **标题**: `<AnimatedGradientText />` (Magic UI)

  - 主标题: "Codeium vs GitHub Copilot"
  - 副标题: "The most intelligent AI code generation tool out there and we have the data to prove it."

- **链接文本**: `<SparklesText />` (Magic UI)

  - 文字: "Read more about the performance quality comparison here >"
  - 使用品牌色 (#00FFB9) 显示

- **对比表格**: `<BorderBeam />` (Magic UI)

  - 表头显示两个产品的 Logo
  - 使用暗色背景突出内容
  - 表格行之间使用细线分隔

- **评分展示**:

  - 使用 `<StarRating />` (自定义组件) 显示评分
  - 五角星使用品牌色 (#00FFB9) 显示
  - 未选中的星星使用暗色显示

- **状态图标**:
  - 使用 `<CheckIcon />` 和 `<CrossIcon />` (自定义组件)
  - 对勾使用品牌色 (#00FFB9)
  - 叉号使用红色 (#FF4040)

### 实现细节

1. **表格布局**

   - 三列布局：特性名称、Codeium、GitHub Copilot
   - 所有行使用一致的高度和内边距
   - 鼠标悬停时突出显示当前行

2. **响应式设计**

   - 在移动设备上转为卡片式布局
   - 保持文本和图标的清晰度

3. **动画效果**
   - 使用 BoxReveal 实现滚动时的渐入效果
   - 表格行 hover 时添加微妙的背景色变化

### 6. 客户评价区

- **容器**: `<Marquee />` (Magic UI)

  - 实现水平滚动效果，展示多条客户评价
  - 设置滚动速度和方向

- **评价卡片**: `<MagicCard />` (Magic UI)
  - 每条评价使用卡片样式，带有阴影和圆角
  - 显示客户头像、姓名、职位、公司 Logo
  - 引用文本内容

### 实现细节

1. **滚动效果**

   - 使用 Marquee 组件实现无缝滚动
   - 设置滚动速度为中等，确保可读性

2. **卡片设计**

   - 使用 MagicCard 提供的渐变效果
   - 卡片内文本居中对齐
   - 使用品牌色突出显示客户姓名和公司

3. **响应式设计**

   - 在移动设备上调整卡片大小和间距
   - 确保滚动效果在所有设备上流畅

4. **可访问性**
   - 为每个评价卡片添加 aria-label
   - 确保文本对比度符合标准

### 7. 行动召唤区 (CTA Section)

- **Logo**: `<MagicCard />` (Magic UI)

  - 显示 codeium.svg
  - 添加悬浮效果和光晕
  - 居中放置

- **标题**: `<AnimatedGradientText />` (Magic UI)

  - 文字: "Get Your Superpowers"
  - 使用大号字体
  - 下方添加动态下划线效果

- **按钮**: `<ShimmerButton />` (Magic UI)
  - 文字: "Get Codeium"
  - 使用品牌主色 (#00FFB9)
  - 添加发光和悬浮效果

### 实现细节

1. **布局设计**

   - 垂直居中布局
   - 元素之间保持适当间距
   - 背景保持简洁的深色调

2. **动画效果**

   - Logo 添加缓慢旋转动画
   - 标题文字使用渐变动画
   - 按钮使用光效动画

3. **响应式设计**

   - 在移动设备上调整元素大小
   - 保持视觉效果的一致性

4. **交互体验**
   - 按钮点击时添加反馈效果
   - 鼠标悬停时增强视觉效果

### 8. 发现更多区 (Discover More Section)

- **标题**: `<AnimatedGradientText />` (Magic UI)

  - 文字: "Discover More"
  - 使用渐变效果，吸引注意

- **信息卡片**: `<MagicCard />` (Magic UI)
  - 每个卡片包含图标、标题、描述和链接
  - 卡片内容：
    1. **Enterprise Plan**
       - 描述: 提供高质量、安全的 AI 工具，支持灵活部署和自托管
       - 链接: "Learn More"
    2. **Training Data**
       - 描述: 不使用非许可代码进行训练，保护用户免受法律风险
       - 链接: "Read More"
    3. **Compare**
       - 描述: 比较 Codeium 与其他 AI 编码工具
       - 链接: "See Comparisons"
    4. **How is this Free?**
       - 描述: Codeium 对个人用户免费
       - 链接: "Read More"
    5. **Security & Privacy**
       - 描述: 提供最佳产品，保护个人数据
       - 链接: "Read More"
    6. **FAQ**
       - 描述: 常见问题解答
       - 链接: "Go to FAQ"

### 实现细节

1. **布局设计**

   - 使用 CSS Grid 创建两行三列布局
   - 卡片之间保持一致的间距

2. **交互效果**

   - 卡片悬停时添加轻微的缩放和阴影效果
   - 链接文字使用品牌色，并在悬停时下划线

3. **响应式设计**

   - 在移动设备上调整为单列布局
   - 确保文本和图标的清晰度

4. **可访问性**
   - 为每个卡片添加 aria-label
   - 确保文本对比度符合标准

### 9. 页脚区 (Footer Section)

- **Logo 区域**: `<MagicCard />` (Magic UI)
  - Codeium logo
  - 标语: "Your modern coding superpowers."
  - 社交媒体图标:
    - Email
    - Twitter
    - Discord
    - LinkedIn
    - Reddit
    - YouTube

- **导航菜单**: `<FooterNav />` (Magic UI)
  - 分为四列导航区域:
    1. **Product**
       - Windsurf Editor
       - Supercomplete
       - Codeium Chat
       - Live
       - Forge
       - Pricing
       - Enterprise
       - Offers

    2. **Extensions**
       - Visual Studio Code
       - JetBrains
       - Neovim / Vim
       - Chrome
       - See All

    3. **Industry**
       - Tech Leaders 2024
       - Blog
       - Careers
       - Contact
       - FAQ

    4. **Company & Support**
       - About Us
       - Community
       - Terms of Service
       - Privacy Policy
       - Media Kit
       - University

- **版权信息**: `<Text />` (Magic UI)
  - "© 2024 Exafunction, Inc. All rights reserved."

### 实现细节

1. **布局设计**
   - 使用网格布局排列导航列
   - 保持列间距一致
   - Logo 区域独立放置

2. **交互效果**
   - 链接悬停时添加淡入效果
   - 社交媒体图标悬停时添加缩放效果

3. **响应式设计**
   - 在移动设备上转为单列布局
   - 保持导航项的清晰度

4. **可访问性**
   - 为所有链接添加合适的 aria 标签
   - 确保导航结构语义化

### 个人信息页

#### 1. 侧边栏

- **头像**: 圆形图标，显示用户首字母
- **用户信息**:
  - 姓名和用户名
  - 会员信息和邮箱
  - PRO 状态标识
- **导航选项**:
  - Bio 编辑按钮
  - 成就展示 (左右切换)
  - 产品更新社交媒体链接 (Twitter, LinkedIn)
  - 功能按钮: 升级到 Pro、推荐朋友、设置、登出

#### 2. 统计展示区

- **统计卡片**:
  - 完成次数 (7天): `<StatCard />` (Magic UI)
  - 总完成次数: `<StatCard />` (Magic UI)
  - 连续记录: `<StatCard />` (Magic UI)
- **交互按钮**:
  - "My Public Profile" 和 "Share" 按钮

#### 3. 活动热图

- **热图展示**: `<HeatMap />` (自定义组件)
  - 显示每周的活动情况
  - 使用颜色深浅表示活跃度

#### 4. 编程语言分布

- **饼图**: `<PieChart />` (自定义组件)
  - 显示用户使用的编程语言比例
  - 图例标识主要语言 (如 TSX)

### 实现细节

1. **布局设计**
   - 使用 Flexbox 布局
   - 侧边栏固定在左侧，内容区占据右侧
   - 统计展示区和图表区垂直排列

2. **交互效果**
   - 侧边栏按钮悬停时显示阴影
   - 统计卡片点击时显示详细信息
   - 热图和饼图支持鼠标悬停提示

3. **响应式设计**
   - 在移动设备上，侧边栏可折叠
   - 统计卡片和图表区在小屏幕上垂直堆叠

4. **视觉效果**
   - 深色主题背景
   - 统一的品牌色 (#00FFB9) 用于高亮
   - 使用现代无衬线字体

## 动画效果实现

### 1. 页面过渡

import { motion } from 'framer-motion';
const pageVariants = {
initial: { opacity: 0, y: 20 },
animate: { opacity: 1, y: 0 },
exit: { opacity: 0, y: -20 }
};

### 2. 滚动动画

使用 Magic UI 的 `<BoxReveal />` 组件实现滚动渐入效果：
<BoxReveal>
<YourComponent />
</BoxReveal>

## 主题系统

使用 `next-themes` 和 Magic UI 的主题系统实现暗色/亮色模式切换：
import { ThemeProvider } from 'next-themes';
const App = ({ children }) => (
<ThemeProvider attribute="class" defaultTheme="dark">
{children}
</ThemeProvider>
);

## 响应式设计

所有组件都基于 Tailwind CSS 的响应式类进行适配：

- sm: 640px
- md: 768px
- lg: 1024px
- xl: 1280px
- 2xl: 1536px

## 性能优化

1. 组件懒加载
   const DynamicComponent = dynamic(() => import('./Component'), {
   loading: () => <LoadingSpinner />
   });
2. 图片优化
   import { Image } from 'next/image';
   <Image
   src="/hero-image.png"
   alt="Hero"
   width={1200}
   height={600}
   priority
   />
```

