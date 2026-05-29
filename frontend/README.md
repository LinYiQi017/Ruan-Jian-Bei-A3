# 🚀 现代化前端开发脚手架底座 (Vue 3 + TypeScript + Tailwind CSS + Element Plus)

这是一个为高效系统研发及大赛项目量身定制的高级前端开发底座。项目不仅保持了极致的轻量与纯净，同时集成了当下最主流、开发体验最舒适的前端技术栈及工程化配置。

---

## 🛠️ 技术栈清单

| 技术 / 工具 | 说明 | 作用 |
| :--- | :--- | :--- |
| **Vue 3** | 最新渐进式 JavaScript 框架 | 使用 `<script setup lang="ts">` 组合式 API 开发 |
| **Vite** | 极速前端构建工具与开发服务器 | 提供秒级的热更新 (HMR) 速度 |
| **TypeScript** | 微软开发的强类型编程语言 | 提供全方位的代码类型安全和 IDE 智能补全 |
| **Tailwind CSS (v4)** | 原子化 / 实用类优先的 CSS 框架 | 无需编写繁琐 CSS，极速构建高度定制化的现代 UI |
| **Element Plus** | Vue 3 经典 B 端组件库 | 提供丰富的交互组件、消息弹窗与表单控件 |
| **Pinia** | 官方推荐的 Vue 3 响应式状态管理库 | 轻量、模块化的全局状态管理 |
| **Vue Router** | Vue 官方路由管理器 | 预配置好路由体系，支持路由懒加载 |
| **Axios** | 易用、成熟的 Promise 网络请求库 | 已封装统一的拦截器体系（支持自动携带 Bearer Token） |
| **VueUse** | 实用的 Vue Composition API 工具集 | 提供数十种开箱即用的响应式浏览器 API 封装 |
| **Lucide Vue** | 极简主义、现代化线条图标库 | 补充 Element Plus 以外的个性化高颜值图标 |
| **Vitest** | Vite 生态首选的高性能测试框架 | 用于极速进行组件单元测试、数据流与状态测试 |
| **Happy DOM** | 轻量级、超高速的浏览器 API 模拟器 | 为测试运行提供沙箱化的虚拟浏览器 DOM 环境 |

---

## 📂 推荐目录结构

为了方便团队协作与高效研发，项目推荐使用如下规范目录：

```text
frontend/
├── src/
│   ├── api/             # 统一管理后端接口调用
│   ├── assets/          # 静态资源（图片、全局字体等）
│   ├── components/      # 通用/可复用 UI 业务组件
│   ├── router/          # Vue Router 路由配置 (src/router/index.ts)
│   ├── stores/          # Pinia 全局状态存储 (src/stores/counter.ts)
│   │   └── counter.test.ts # 单元测试文件示例
│   ├── utils/           # 通用工具函数与网络请求 (src/utils/request.ts)
│   ├── views/           # 页面级组件 (HomeView, AboutView 等)
│   ├── App.vue          # 单页面入口骨架 Shell
│   ├── main.ts          # 脚手架挂载与库注册入口
│   └── style.css        # Tailwind CSS 及全局样式声明
├── tsconfig.json        # TypeScript 编译配置
├── vite.config.ts       # Vite 配置文件（已集成 Tailwind、Vitest 与 @/ 别名）
└── package.json         # 项目依赖及运行指令
```

---

## 🔧 核心开发规范

### 1. 路径别名 (Path Alias)
项目已内置配置路径别名，使用 `@/` 可直接指向 `src/` 目录：
```ts
import { useCounterStore } from '@/stores/counter'
```

### 2. 状态管理 (Pinia Store)
采用 Vue 3 官方推荐的 **Setup 语法** 编写，直观高效：
```ts
export const useCounterStore = defineStore('counter', () => {
  const count = ref(0)
  const increment = () => count.value++
  return { count, increment }
})
```

### 3. 网络请求 (Axios Wrapper)
预置的 `src/utils/request.ts` 会自动拦截请求并在 `Authorization` 头中附加 `localStorage` 内的 `token`。

---

## 🧪 测试与质量保障

项目已原生集成 **Vitest** + **Happy DOM** 测试环境，且配置了全局类型支持。

### 运行测试
* **实时监听模式** (开发时代码保存自动重测)：
  ```bash
  npm run test
  ```
* **单次运行模式** (用于持续集成与代码发布前自检)：
  ```bash
  npm run test:run
  ```

### 编写测试用例
测试文件推荐存放在所测试的源文件同级或邻级，并以 `*.test.ts` 或 `*.spec.ts` 命名。
例如项目中预置的 **Pinia Store 单元测试** (`src/stores/counter.test.ts`)：
```ts
import { describe, it, expect, beforeEach } from 'vitest'
import { setActivePinia, createPinia } from 'pinia'
import { useCounterStore } from './counter'

describe('Counter Store', () => {
  beforeEach(() => {
    setActivePinia(createPinia())
  })

  it('increments the count', () => {
    const counter = useCounterStore()
    expect(counter.count).toBe(0)
    counter.increment()
    expect(counter.count).toBe(1)
  })
})
```

---

## 🚀 启动与部署

### 1. 安装依赖
```bash
npm install
```

### 2. 启动开发服务器
```bash
npm run dev
```

### 3. 生产环境构建与类型检查
```bash
npm run build
```
*(构建产物将输出在 `dist/` 文件夹中)*
