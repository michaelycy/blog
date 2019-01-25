## XML 类型文件下载

下载xml文件大多浏览器模型的行为都是浏览，而并不是下载，其实想要解决这个问题很简单只需要为response header中添加 `Content-Type`设置为`application/octet-stream`,同时设置`Content-Disposition`为`attachment`


    application/octet-stream：将其保存到文件中

    Content-Disposition：消息头指示回复的内容该以何种形式展示,内联（inline）、附件（attachment），其中attachment时浏览器呈现为“另存为”的对话框，将filename的值预填为下载后的文件名，假如它存在的话）
    
    
故`nginx`配置为:
``` nginx
location ~* \/assets\/(\w)+\.xml$ {
      root   /usr/share/nginx/html/;
      add_header Content-Type application/octet-stream;
      add_header Content-Disposition attachment;
}
```
通过这样配置以后就会匹配所以assets文件夹下的xml文件，并且为其添加头信息。这样浏览器就会默认使用另存了，即下载；