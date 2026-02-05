# Wikidot SiteProxy For VPS
解决某些网络环境下wikidot访问受限的问题。 利用GO作为后端，重写发送的HTML代理服务通过域名映射和资源转发，最终实现整站网页资源接管。
# 部署服务
### 1.安装Golang
     apt install golang
### 2. 下载文件 config.go 并按需修改配置文件,与 go.mod 放置在vps你新建的文件夹中
    // 域名映射配置
    var domainMappings = map[string]string{
    "ci-cn-wiki.wikidot.com":                    "ci.",
    "d3g0gp89917ko0.cloudfront.net": "cloudfront-com.",
    "scp-wiki.wdfiles.com":       "scp-wiki-com.",
    "ci-wiki-intl.wdfiles.com":          "ci-intl-com.",
    "www.wikidot.com":                "wikidot-com.",
    "ci-cn-wiki.wdfiles.com":     "ci-cn-wiki-wdfiles-com.",
    "cdn.onesignal.com":    "cdn.",
    "fonts.gstatic.com":                     "fonts.",
    "ci-theme.wdfiles.com":         "ci-theme.",
    }
### 3.运行
    go run .
  <h4>若输出以下日志则成功</h4>	
    
    代理服务器启动在端口8080
    请确保你的域名已正确配置并指向此服务器
### 4.配置域名
  使用Nginx或OpenResty反向代理 localhost:8080。并利用DNS你的域名泛解析到你的服务器。
# 补充
  1.映射配置后面所代表的即为你的域名前缀<br>
  2.需要利用supervisor等进程保护工具维持进程的运行<br>
  3.第四步可以利用1panel等面板进行操作
  
