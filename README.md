# -## 工程化相关

### 配置分包

将业务代码与第三方包代码分离开打包，可以利用缓存优化，因为第三方包一般变化较少，所以可以读取缓存

vite进行配置

```
import { defineConfig } from "vite";
import vue from "@vitejs/plugin-vue";

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue()],
  build: {
  //因为是打包构建时的配置，所以在rollup里面
    rollupOptions: {
      output: {
        manualChunks(id) {
          if (id.includes("node_modules")) {
            return "vendor";
          }
        },
      },
    },
  },
});


```

### 检查依赖

```
npm i depcheck -g
depcheck
npx depcheck

```

![image-20240513174522435](C:\Users\13328\AppData\Roaming\Typora\typora-user-images\image-20240513174522435.png)

## js知识

### 动态加载js代码

```
const a = `const a = 1; console.log('hello world',a)`
//如何执行a
new Function(a)()
```

## 可视化相关

### 屏幕适配方案

autofit.js原理：利用scale放大缩小实现

利用rem px方案
