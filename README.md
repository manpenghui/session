# session
node express框架下，跨域session的设置问题


在前后端完全分离，各起一套服务的情况下，产生了跨域问题，此时虽然前端起了代理，但后端依然无设置session，这是因为session是基于cookie的，而cookie是不允许跨域的，因此要解决开发环境下的解决session的问题可以通过下面的方法解决。

  1.
```
app.all('*', function(req, res, next) {  
   res.header("Access-Control-Allow-Origin", "*");  
   res.header("Access-Control-Allow-Headers", "X-Requested-With");  
   res.header("Access-Control-Allow-Methods","PUT,POST,GET,DELETE,OPTIONS");  
   res.header("X-Powered-By",' 3.2.1')  
   res.header("Content-Type", "application/json;charset=utf-8");  
   next();  
});  
```
  2.
可以设置一个nginx或者什么别的来做一下转发，避免跨域。
可以弄一个nginx，设置8080，然后app指向3000，api指向1994。
或者不使用session，而使用token来做api请求
