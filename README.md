# 基于 vue-cli 3.0.0 构建的多页面基础项目模板

前言

---

> 该项目跑了下 `vue-cli 3.0.0` 多页面项目创建的流程，就当个以后多页项目的雏形了，新版的 `vue-cli` 已经默认可以支持多页面构建了（不需要之前版本的那种修改 `webpcak` 配置文件了），可以共用放在 `src` 目录下的 `store.js` 里面的数据

效果 GIF 图

---

> ![效果.gif](https://upload-images.jianshu.io/upload_images/9064013-9b433b4901fbc83e.gif?imageMogr2/auto-orient/strip)

参考资料

---

- [vue-cli 整体官方文档](https://cli.vuejs.org/guide/)

- [vue-cli 3.0.0 安装](https://cli.vuejs.org/guide/creating-a-project.html#installation)

- [vue-cli 多页面的配置方法](https://cli.vuejs.org/config/#pages)
  注意：这里的 `vue.config.js` 配置文件是需要自行创建的，与 `package.json` 一样存在于项目根目录

- [vue.config.js 配置文件官方介绍](https://cli.vuejs.org/config/#vue-config-js)

运行方法（nodejs 版本建议 8.10.0 以上）

---

- 装包

  ```shell
  # 先得全局安装 vue-cli 3.0.0 已安装的请忽略此步骤
  npm install -g @vue/cli
  # OR
  yarn global add @vue/cli

  # 本项目安装依赖
  yarn
  # OR
  npm install
  ```

- 运行

  ```
  # 开发
  npm run serve

  # 生产
  npm run build
  ```

主要修改的地方

---

- 将之前默认的路径改为以 `@` 为地址的索引
  > ![image.png](https://upload-images.jianshu.io/upload_images/9064013-f68f00de655ae06f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  > ![image.png](https://upload-images.jianshu.io/upload_images/9064013-d91ea67d028df791.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 新建 `index` 和 `subpage` 文件夹，内部的文件结构与之前 `SPA` 基本一致，只是将 `store.js` 文件单独提了重来以便数据公用
- 重点就是新建的 `vue.config.js` 配置文件里面的内容，源码和注释如下所示

  ```javascript
  // vue.config.js
  module.exports = {
    pages: {
      index: {
        // 页面的入口文件
        entry: 'src/index/main.js',
        // 页面的模板文件
        template: 'public/index.html',
        // build 生成的文件名称  例： dist/index.html
        filename: 'index.html'
      },
      // template 默认会去找 public/subpage.html 页面，如果找不到会使用 public/index.html 文件
      // 输出文件会默认的推断为 subpage.html
      subpage: 'src/subpage/main.js'
    }
  }
  ```
