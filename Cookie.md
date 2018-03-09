# Cookie
## Cookie是什么
在HTTP协议的定义中，采用了一种机制来记录客户端和服务器端交互的信息，这种机制被称为Cookie，

## Cookie的特性
Cookie规范定义了服务器和客户端交互信息的格式、有效期、使用范围、安全性。Cookie也可以叫做浏览器缓存。

Cookie储存在用户本地终端（Client Side）特定目录下的数据（通常经过加密）,保存的Cookie文件名中会包含创建Cookie所在页面网站的域名，当浏览器再次连接该网站时，会从本机Cookie存放目录下选出该网站的有效Cookie，将保存在其中的信息附加在HTTP消息头中发送到服务器端，服务器端程序就可根据上次保存在Cookie的信息为访问客户提供“记忆”或个性化服务。

## 应用场景
由于http是无状态的，比如在淘宝的某个页面中，你进行了登陆操作。当你跳转到商品页时，服务端如何知道你是已经登陆的状态？这个时候就需要用到Cookie。
或者说存储一些不是很敏感的信息，或者进行登录控制，也可用来记住用户名、记住免密码登录、防止刷票等。

详细叙述可以这样说~  
具体来讲用于采用HTTP作为进行信息交换协议的客户端和服务器端用于记录需要持久化的信息。一般是由服务器端创建要记录的信息，然后传递到客户端，由客户端从HTTP消息中取出信息，保存在本机磁盘上。当客户端再次访问服务器端时，从本机磁盘上读出原来保存的信息，附加到HTTP消息中发送给服务器端，服务器端从HTTP消息中读取信息，根据实际应用的需求进行进一步的处理。

## 缺点
- 传输  
在客户端和服务器端交互过程中，Cookie信息被附加在HTTP消息头中传递，所以Cookie信息过多的话会影响传输效率

- 不安全  
由于是存储在客户端的数据，Cookie 可能会被篡改

- 大小限制  
每个域名下允许的Cookie是有限制的，根据浏览器这个限制也不同。一个域名的每个Cookie限制以4千字节（KB）键值对的形式存储。

- 限制  
用户配置为禁用 有些用户禁用了浏览器或客户端设备接收Cookie的能力，因此限制了这一功能。

## Cookie设置
一个cookie只能包含一个自定义键/值对。Cookie本身属性有”Comment” 、”Domain”、”Max-Age”、”Path”、”Secure”、”Version”。

Comment 属性是cookie的产生着对该cookie的描述；

Domain 属性定义可访问该cookie的域名，对一些大的网站，如果希望cookie可以在子网站中共享，可以使用该属性。例如设置Domain为http://bigsite.com ,则http://sub1.bigsite.com和http://sub2.bigsite.com都可以访问已保存在客户端的cookie，这时还需要将Path设置为/。

Max-Age 属性定义cookie的有效时间，用秒计数，当超过有效期后，cookie的信息不会从客户端附加在HTTP消息头中发送到服务端。

Path 属性定义网站上可以访问cookie的页面的路径，缺省状态下Path为产生cookie时的路径，此时cookie可以被该路径以及其子路径下的页面访问；可以将Path设置为/，使cookie可以被网站下所有页面访问。

Secure 属性值定义cookie的安全性，当该值为true时必须是HTTPS状态下cookie才从客户端附加在HTTP消息中发送到服务端，在HTTP时cookie是不发送的；Secure为false时则可在HTTP状态下传递cookie，Secure缺省为false。

Version 属性定义cookie的版本，由cookie的创建者定义。

<br>
**服务端设置 cookie**  
通常使用 HTTP 协议规定的 set-cookie 头操作。
规范规定 cookie 的格式为 name = value 格式，且必须包含这部分。


