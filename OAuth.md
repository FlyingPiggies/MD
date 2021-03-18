# OAuth 2.0

OAuth 2.0是OAuth协议的延续版本，但不向前兼容OAuth 1.0。

OAuth是目前最流行的授权机制，用来授权第三方应用，获取用户的数据。

## 授权方式 - 获取令牌

***

1.	授权码（authorization code）  

	grant_type = authorization_code

	第三方应用先申请一个授权码，然后再用授权码获取令牌（token）。
	适用于前后端分离的应用。

![authorization code](https://www.wangbase.com/blogimg/asset/201904/bg2019040905.jpg)

2.	隐藏式（implicit）  

	grant_type = token

	有些web应用是纯前端应用，没有后端。这是就不能使用上面的方式了，必须将令牌存储在前端。

![](https://www.wangbase.com/blogimg/asset/201904/bg2019040906.jpg)

3.	密码式（password）

	grant_type = password

	直接允许用户将自己的用户名密码告诉三方应用。

4.	凭证式（client credentials）

	grant_type = client_credentials

	使用于没有前端的命令行应用，即在命令下请求令牌。


## 令牌的使用

***

在请求的Header中，加上一个Authorization字段，令牌就放在这个字段中。

## 更新令牌

***

网站在颁发令牌的时候，一次性颁发两个令牌，一个用于获取数据，一个用于更新令牌

grant_type = refresh_token

## 令牌的实现方式

### JWT - Json Web Tokens

是一种基于Json用于安全的信息传输标准。  

两个用途：
- 数据交互，保证数据的完整性。
- 携带用户信息进行身份验证。

三个部分：
- header  
	包含了签名算法，及令牌类型  
	
	{
		"alg" : "HS256",
		"typ" : "JWT"
	}

- payload  
	包含了jwt所携带的信息内容

	{
		"sub" : "1234567890",
		"name" : "Qu Jin"
	}

- signature
	包含了header以及payload的base64编码后的结果


# OAuth 与 OpenId Connect

OpenId Connect 是在 OAuth 2.0 协议之上的标识层。它拓展了 OAuth 2.0，使得认证方式标准化。

![](https://static001.infoq.cn/resource/image/23/8c/238ca4bd4fbe2279397e50cbb951be8c.png)

OAuth 不会提供用户身份，而是会提供用于授权的访问令牌。OpenId Connect 使客户端能够通过认证来识别用户，其中认证在授权服务端执行。它是这样实现的：在向授权服务端发起用户登录和授权告知的请求时，定义一个名叫openid的授权范围。在告知授权服务器需要使用 OpenId Connect时，OpenId是必须存在的范围。


# OAuth 与 SSO

单点登录（SingleSignOn）就是通过用户的一次性鉴别登录。当用户在身份认证服务上登录一次以后，即可获得访问单点登录系统中其他管理系统和软件的权限，同时这种实现是不需要管理员对用户的登陆状态或其他消息进行更改的，这意味着在多个应用系统中，用户只需一次登录就可以访问所有相互信任的系统。这种方式减少了由登录产生的时间消耗，辅助了用户管理。



