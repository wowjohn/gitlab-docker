gitlab搭建
================

* 使用docker-compose.yml组织配置内容
* 同时搭建了gitlab-runner


相关事项
-----------

* 运行docker-compose up -d (启动比较慢，一般需要2分钟)

### 配置邮箱
*  gitlab_rails['gitlab_email_enabled'] = true
*  gitlab_rails['gitlab_email_from'] = '29@qq.com'
*  gitlab_rails['gitlab_email_display_name'] = 'jimu'
*  gitlab_rails['gitlab_email_reply_to'] = '29@qq.com'
*  gitlab_rails['smtp_enable'] = true
*  gitlab_rails['smtp_address'] = "smtp.qq.com"
*  gitlab_rails['smtp_port'] = 25
*  gitlab_rails['smtp_user_name'] = "29@qq.com"
*  gitlab_rails['smtp_password'] = "***"
*  gitlab_rails['smtp_domain'] = "qq.com"
*  gitlab_rails['smtp_authentication'] = login
*  gitlab_rails['smtp_enable_starttls_auto'] = true
*  gitlab_rails['smtp_tls'] = false

> 添加进 gitlab.rb 中，运行docker exec -it gitlab gitlab-ctl reconfigure 重新加载配置文件即可

### 注册gitlab-runner
* 访问虚拟域名,找到路径为 Admin area => Overview => Runners 下的对应的URL和token
* 运行 docker exec -it gitlab-runner gitlab-runner register
* 填入对应信息即可
* 刷新网页即可看到下方的runner

### 备注
> 虚拟域名为 my.gitlab.com
> 初次登录需要键入超级管理员密码，用户名默认为root
> docker pull gitlab镜像时，提示需要登录，键入docker-login ,账户名选择docker的用户名，不能是邮箱！！！不能是邮箱！！！不能是邮箱！！！（为了这个问题折腾了好久）
