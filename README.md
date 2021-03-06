# OneIndex - TZG
一个 OneIndex 分支改进版，保留原版的简洁。 
原项目：[donwa/oneindex](https://github.com/donwa/oneindex)

## 功能：
不占用服务器空间，不走服务器流量，   
直接列出 OneDrive 目录，文件直链下载。  

## 示例站
[TZG OneDrive](https://tzg6.app)   

## 跳转页面
oneindex-tzg 使用了自己的跳转页面进行跳转。如果你希望搭建一个自己的跳转页面，请前往[TheZihanGu/OneIndex-TZG-Jump-page](https://github.com/TheZihanGu/OneIndex-TZG-Jump-page)进行查看。

## 安装运行

### 最低配置：
* PHP 5.6+ 需打开curl支持   
* OneDrive 账号 (个人、企业版或教育版/工作或学校帐户), 暂不支持世纪互联代理   
* oneindex-tzg 程序   
* 除中国大陆外的服务器/虚拟主机一台。建议使用[阿里云ECS](https://promotion.aliyun.com/ntms/act/qwbk.html?userCode=4wz5xqgf)进行搭建。   

## 配置：
<img width="658" alt="image" src="https://raw.githubusercontent.com/donwa/oneindex/files/images/install.gif">  

### 计划任务  
[可选]**推荐配置**，非必需。后台定时刷新缓存，可增加前台访问的速度。  
```
# 每小时刷新一次token
0 * * * * /具体路径/php /程序具体路径/one.php token:refresh

# 每十分钟后台刷新一遍缓存
*/10 * * * * /具体路径/php /程序具体路径/one.php cache:refresh
```

## 特殊文件实现功能  
` README.md `、`HEAD.md` 、 `.password`特殊文件使用  

可以参考[https://github.com/donwa/oneindex/tree/files](https://github.com/donwa/oneindex/tree/files)  

**在文件夹底部添加说明:**  
>在 OneDrive 的文件夹中添加` README.md `文件，使用 Markdown 语法。  

**在文件夹头部添加说明:**  
>在 OneDrive 的文件夹中添加`HEAD.md` 文件，使用 Markdown 语法。  

**加密文件夹:**  
>在 OneDrive 的文件夹中添加`.password`文件，填入密码，密码不能为空。  

**直接输出网页:**  
>在 OneDrive 的文件夹中添加`index.html` 文件，程序会直接输出网页而不列目录。  
>配合 文件展示设置-直接输出 效果更佳。  

## 命令行功能  
仅能在PHP CLI模式下运行  

**清除缓存:**  
```
php one.php cache:clear
```
**刷新缓存:**  
```
php one.php cache:refresh
```
**刷新令牌:**  
```
php one.php token:refresh
```
**上传文件:**  
```
php one.php upload:file 本地文件 [OneDrive文件]
```


**上传文件夹:**  
```
php one.php upload:folder 本地文件夹 [OneDrive文件夹]
```

例如：  
```
//上传demo.zip 到OneDrive 根目录  
php one.php upload:file demo.zip  

//上传demo.zip 到OneDrive /test/目录  
php one.php upload:file demo.zip /test/  

//上传demo.zip 到OneDrive /test/目录并将其命名为 d.zip  
php one.php upload:file demo.zip /test/d.zip  

//上传up/ 到OneDrive /test/ 目录  
php one.php upload:file up/ /test/
```
