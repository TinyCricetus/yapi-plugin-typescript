# yapi-plugin-typescript



该插件为 YApi 页面的 Chrome 插件，用于为数据自动生成 TS 的接口声明，效果如下图所示：

![示例1](./images/1.png)

![示例2](./images/2.png)



## 先决条件



- [node 18.16.0](https://nodejs.org/en)
- node 自带了 **npm** 包管理工具，如果想使用 **pnpm** 管理，需要全局安装：
```sh
npm install -g pnpm
```



## 使用说明
先克隆本项目至本地，然后按照以下操作步骤进行使用。



### 安装依赖
克隆本项目至本地后，使用以下命令安装依赖：
```sh
npm install

// 或者
pnpm install
```



### 作用域修改
Chrome 的插件需要指定可运行的目前网页，修改方式为：
1. 找到目录下 **manifest.json** 配置文件；
2. 修改 **matches** 配置字段中的页面链接匹配，以匹配需要作用的域名；
3. 修改 main.ts 中的 api 请求前缀 **API_PREFIX** 。

例如：需要把插件用于页面 www.test.com 需要在 **manifest.json** 文件中做出如下修改：


```json
"matches": [
  "https://www.test.com/*"
]
```
> 注意：使用通配符 * 来匹配该页面下的所有路径。



```typescript
// main.ts
const API_PREFIX = 'https://www.test.com/api/interface/get?id='
```



### 构建插件
运行：
```sh
npm build

// 或者
pnpm build
``` 
插件将完成构建，注意构建完成后目录将会出现一个 dist 目录。



### 加载插件
插件需要浏览器的扩展程序进入开发者模式，然后按照路径 **扩展管理 -> 已安装扩展 -> 加载已安装扩展** 来加载扩展，加载前需确保插件构建成功，如果已经完成构建，选择 **dist** 文件夹即可加载。



