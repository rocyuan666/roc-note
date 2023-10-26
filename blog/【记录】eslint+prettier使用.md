# 介绍

需要使用到以下四个库：
eslint：用来检查js代码质量
prettier：用来格式化美化代码风格
eslint-plugin-prettier：按 eslint 规则运行 prettier
eslint-config-prettier：关闭 eslint 与 prettier 冲突的规则

# 安装

分别安装 eslint、prettier、eslint-plugin-prettier、eslint-config-prettier

```bash
npm i -D eslint prettier eslint-plugin-prettier eslint-config-prettier
```

# 配置文件

eslint配置文件：.eslintrc.js

```javascript
module.exports = {
  extends: ['prettier'],
  plugins: ['prettier'],
  rules: {
    'prettier/prettier': [
      'error',
      {
        endOfLine: 'auto',
      },
    ],
  },
}

```

prettier配置文件：.prettierrc.json

```json
{
  "semi": false,
  "tabWidth": 2,
  "useTabs": false,
  "singleQuote": true,
  "jsxSingleQuote": false,
  "printWidth": 100,
  "endOfLine": "lf"
}

```

# 脚本定义

定义格式化代码脚本，方便格式化全部代码，打开 package.json，定义 format 脚本
--write . 格式化全部代码
--write src/ 格式化 src 目录下代码
......

```json
{
  "scripts": {
    "format": "prettier --write ."
  },
  "devDependencies": {
    "eslint": "^8.51.0",
    "eslint-config-prettier": "^9.0.0",
    "eslint-plugin-prettier": "^5.0.0",
    "prettier": "^3.0.3"
  }
}
```

# vscode保存自动格式化配置

根目录创建 .vscode 文件夹，创建 settings.json 配置文件

```json
{
  "editor.codeActionsOnSave": {
    // 保存使用eslint进行修复（格式化）代码
    "source.fixAll.eslint": true
  }
}

```
