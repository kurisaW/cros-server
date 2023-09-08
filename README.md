# cros-server

项目主要解决国内的 https://cors-anywhere.azm.workers.dev/https://github.com/login/oauth/access_token 接口被墙导致 [gitalk 无法获取 token 问题](https://github.com/gitalk/gitalk/issues/514)

## 接口部署

### netlify

fork项目到自己的github账号下,在netlify选择"Add new site"->"import an existing project"即可

部署完可以通过修改默认域名

## 使用cdn

### hexo+next主题

```yml
#source/data/next.yml配置文件中修改配置,将url替换为要使用的加速文件连接
# Gitalk
#gitalk_js: //cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js
#gitalk_css: //cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.css
```

在gitalk.min.js中将
```js
proxy:"https://cors-anywhere.azm.workers.dev/https://github.com/login/oauth/access_token"
```

修改为自部署的接口如
```js
proxy:"https://proxy-gitalk-api.netlify.app/github_access_token"
```