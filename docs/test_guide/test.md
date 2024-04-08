访问 iam-apiserver 的 Token，请求如下 API 访问：
$ curl -s -XPOST -H'Content-Type: application/json' -d'{"username":"admin","password":"Admin@2021"}' http://127.0.0.1:8080/login | jq -r .token
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE2MTc5MjI4OTQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE2MTc4MzY0OTQsInN1YiI6ImFkbWluIn0.9qztVJseQ9XwqOFVUHNOtG96-KUovndz0SSr_QBsxAA


代码中下面的 HTTP 请求通过-H'Authorization: Bearer ' 指定认证头信息，将上面请求的 Token 替换 。


用户 CURD创建用户、列出用户、获取用户详细信息、修改用户、删除单个用户、批量删除用户，请求方法如下：

# 创建用户
$ curl -s -XPOST -H'Content-Type: application/json' -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' -d'{"password":"User@2021","metadata":{"name":"xiangyu"},"nickname":"xiangyu","email":"xiangyu@foxmail.com","phone":"185xxxx0812"}' http://127.0.0.1:8080/v1/users

# 列出用户
$ curl -s -XGET -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' 'http://127.0.0.1:8080/v1/users?offset=0&limit=10'

# 获取 colin 用户的详细信息
$ curl -s -XGET -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' http://127.0.0.1:8080/v1/users/xiangyu

# 修改 colin 用户
$ curl -s -XPUT -H'Content-Type: application/json' -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' -d'{"nickname":"xiangyu","email":"xiangyu_cai@foxmail.com","phone":"1851014xxxx"}' http://127.0.0.1:8080/v1/users/xiangyu

# 删除 colin 用户
$ curl -s -XDELETE -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE2MTc5MjI4OTQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE2MTc4MzY0OTQsInN1YiI6ImFkbWluIn0.9qztVJseQ9XwqOFVUHNOtG96-KUovndz0SSr_QBsxAA' http://127.0.0.1:8080/v1/users/colin

# 批量删除用户
$ curl -s -XDELETE -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE2MTc5MjI4OTQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE2MTc4MzY0OTQsInN1YiI6ImFkbWluIn0.9qztVJseQ9XwqOFVUHNOtG96-KUovndz0SSr_QBsxAA' 'http://127.0.0.1:8080/v1/users?name=colin&name=mark&name=john'


密钥 CURD创建密钥、列出密钥、获取密钥详细信息、修改密钥、删除密钥请求方法如下：


# 创建 secret0 密钥
$ curl -s -XPOST -H'Content-Type: application/json' -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' -d'{"metadata":{"name":"secret2"},"expires":0,"description":"admin secret"}' http://127.0.0.1:8080/v1/secrets

# 列出所有密钥
$ curl -s -XGET -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' http://127.0.0.1:8080/v1/secrets

# 获取 secret0 密钥的详细信息
$ curl -s -XGET -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' http://127.0.0.1:8080/v1/secrets/secret0

# 修改 secret0 密钥
$ curl -s -XPUT -H'Content-Type: application/json' -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' -d'{"metadata":{"name":"secret0"},"expires":0,"description":"admin secret(modified)"}' http://127.0.0.1:8080/v1/secrets/secret0

# 删除 secret0 密钥
$ curl -s -XDELETE -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' http://127.0.0.1:8080/v1/secrets/secret0


这里我们要注意，因为密钥属于重要资源，被删除会导致所有的访问请求失败，所以密钥不支持批量删除。


授权策略 CURD创建策略、列出策略、获取策略详细信息、修改策略、删除策略请求方法如下：

# 创建策略
$ curl -s -XPOST -H'Content-Type: application/json' -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' -d'{"metadata":{"name":"policy66"},"policy":{"description":"One policy to rule them all.","subjects":["users:<peter|ken>","users:maria","groups:admins"],"actions":["delete","<create|update>"],"effect":"allow","resources":["resources:articles:<.*>","resources:printer"],"conditions":{"remoteIPAddress":{"type":"CIDRCondition","options":{"cidr":"192.168.0.1/16"}}}}}' http://127.0.0.1:8080/v1/policies

# 列出所有策略
$ curl -s -XGET -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' http://127.0.0.1:8080/v1/policies

# 获取 policy0 策略的详细信息
$ curl -s -XGET -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' http://127.0.0.1:8080/v1/policies/policy66

# 修改 policy0 策略
$ curl -s -XPUT -H'Content-Type: application/json' -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' -d'{"metadata":{"name":"policy66"},"policy":{"description":"One policy to rule them all(modified by caicai).","subjects":["users:<peter|ken>","users:maria","groups:admins"],"actions":["delete","<create|update>"],"effect":"allow","resources":["resources:articles:<.*>","resources:printer"],"conditions":{"remoteIPAddress":{"type":"CIDRCondition","options":{"cidr":"192.168.0.1/16"}}}}}' http://127.0.0.1:8080/v1/policies/policy66

# 删除 policy0 策略
$ curl -s -XDELETE -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' http://127.0.0.1:8080/v1/policies/policy0




# 测试 iam-authz-server

1. 重新登陆系统，并获取访问令牌

curl -s -XPOST -H'Content-Type: application/json' -d'{"username":"admin","password":"Admin@2021"}' http://127.0.0.1:8080/login


2. 创建授权策略

curl -s -XPOST -H"Content-Type: application/json" -H"Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTQwMTAsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1Njc2MTAsInN1YiI6ImFkbWluIn0._YY8TL5iBC8sa8gJv9Dti3SmnLArMO1O211fFaqbKBQ" -d'{"metadata":{"name":"policy88"},"policy":{"description":"One policy to rule them all.","subjects":["users:<peter|ken>","users:maria","groups:admins"],"actions":["delete","<create|update>"],"effect":"allow","resources":["resources:articles:<.*>","resources:printer"],"conditions":{"remoteIPAddress":{"type":"CIDRCondition","options":{"cidr":"192.168.0.1/16"}}}}}' http://127.0.0.1:8080/v1/policies


    修改授权策略
    curl -s -XPUT -H'Content-Type: application/json' -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTIwNjQsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1NjU2NjQsInN1YiI6ImFkbWluIn0.Ryzb12-fmuNBAj724CEjkJbz7bhDp9yFQrXDLTH3x6Q' -d'{"metadata":{"name":"policy88"},"policy":{"description":"One policy to rule them all(modified by caicai).","subjects":["users:<peter|ken>","users:xiangyu","groups:admins"],"actions":["delete","<create|update>"],"effect":"allow","resources":["resources:articles:<.*>","resources:printer"],"conditions":{"remoteIPAddress":{"type":"CIDRCondition","options":{"cidr":"192.168.0.1/16"}}}}}' http://127.0.0.1:8080/v1/policies/policy88



3. 创建密钥，并从命令的输出中提取 secretID 和 secretKey

curl -s -XPOST -H"Content-Type: application/json" -H"Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXBpLm1hcm1vdGVkdS5jb20iLCJleHAiOjE3MTI2NTQwMTAsImlkZW50aXR5IjoiYWRtaW4iLCJpc3MiOiJpYW0tYXBpc2VydmVyIiwib3JpZ19pYXQiOjE3MTI1Njc2MTAsInN1YiI6ImFkbWluIn0._YY8TL5iBC8sa8gJv9Dti3SmnLArMO1O211fFaqbKBQ" -d'{"metadata":{"name":"secret88"},"expires":0,"description":"admin secret"}' http://127.0.0.1:8080/v1/secrets

4.生成访问 iam-authz-server 的 token

iamctl 提供了 jwt sigin 命令，可以根据 secretID 和 secretKey 签发 Token，方便你使用:

iamctl jwt sign ZuxvXNfG08BdEMqkTaP41L2DLArlE6Jpqoox 7Sfa5EfAPIwcTLGCfSvqLf0zZGCjF3l8 # iamctl jwt sign $secretID $secretKey，替换成上一步创建的密钥对

5. 测试资源授权是否通过

我们可以通过请求 /v1/authz 来完成资源授权：
curl -s -XPOST -H'Content-Type: application/json' -H'Authorization: Bearer eyJhbGciOiJIUzI1NiIsImtpZCI6IjFCdzY3NW9JaDd3bnQyaW8zaTkwZERVa3pRcTJBZjNCM0IwcyIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJpYW0uYXV0aHoubWFybW90ZWR1LmNvbSIsImV4cCI6MTcxMjU3NTA0NSwiaWF0IjoxNzEyNTY3ODQ1LCJpc3MiOiJpYW1jdGwiLCJuYmYiOjE3MTI1Njc4NDV9.3uq7oWa-0gP2VjXYDMltKdfXfeBMv-uZjav61ZGVjwQ' -d'{"subject":"users:xiangyu","action":"delete","resource":"resources:articles:ladon-introduction","context":{"remoteIPAddress":"192.168.0.5"}}' http://127.0.0.1:9090/v1/authz


如果授权通过会返回：{"allowed":true}