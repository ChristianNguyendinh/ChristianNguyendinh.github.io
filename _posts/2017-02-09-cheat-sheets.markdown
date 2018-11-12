---
layout: post
title:  "Cheat Sheets"
date:   2017-02-09 15:52:06 -0400
categories: uncategorized
---

<h3><strong>SQL(ite3)</strong></h3>
- https://nineteenthbestfoxinbrookevillemd.wordpress.com/2017/01/14/sql-notes/
<h3><strong>Socket.io </strong></h3>
<strong>- </strong>Kent Aguilar - http://stackoverflow.com/questions/32674391/io-emit-vs-socket-emit

{% highlight javascript %}
socket.emit('message', "this is a test"); //sending to sender-client only
socket.broadcast.emit('message', "this is a test"); //sending to all clients except sender
socket.broadcast.to('game').emit('message', 'nice game'); //sending to all clients in 'game' room(channel) except sender
socket.to('game').emit('message', 'enjoy the game'); //sending to sender client, only if they are in 'game' room(channel)
socket.broadcast.to(socketid).emit('message', 'for your eyes only'); //sending to individual socketid
io.emit('message', "this is a test"); //sending to all clients, include sender
io.in('game').emit('message', 'cool game'); //sending to all clients in 'game' room(channel), include sender
io.of('myNamespace').emit('message', 'gg'); //sending to all clients in namespace 'myNamespace', include sender
socket.emit(); //send to all connected clients
socket.broadcast.emit(); //send to all connected clients except the one that sent the message
socket.on(); //event listener, can be called on client to execute on server
io.sockets.socket(); //for emiting to specific clients
io.sockets.emit(); //send to all connected clients (same as socket.emit)
io.sockets.on() ; //initial connection from a client.
{% endhighlight %}
<!--more-->

JS Arrays (Similar function in other langs)

https://gist.github.com/ourmaninamsterdam/1be9a5590c9cf4a0ab42
<h3>JS ES6</h3>
http://imgur.com/Nx7WJvZ
<h3>Bootstrap 3</h3>
https://bootstrapcreative.com/resources/bootstrap-3-css-classes-index/
<h3>Git</h3>
https://www.git-tower.com/blog/content/posts/54-git-cheat-sheet/git-cheat-sheet-large01.png


