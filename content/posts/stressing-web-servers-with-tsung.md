---
title: Stressing servers with Tsung
date: '2006-09-15T21:47:55+00:00'
slug: stressing-web-servers-with-tsung
categories:
- Erlang
- Planet GPUL
- Planet Igalia
- Yaws
wp_id: 9
---

<a target="_blank" title="Tsung" href="http://tsung.erlang-projects.org/">Tsung</a> is a testing tool used to stress servers and see how they perform under high load conditions. It's designed to work both with the HTTP/HTTPS and the Jabber protocols, and it seems that stressing PostgreSQL servers will be another feature in a near future (still experimental). Tsung is able, for instance, to simulate hundreds of users from a single CPU working as clients of a <em>client-server</em> aplication, in order to stress the server with high load and see how it works under such those contidions.

A very interesting issue about Tsung is that it was written using the <a title="Erlang/OTP" target="_blank" href="http://www.erlang.org"><em>Erlang</em></a> language, which was designed for being used on some kind of environments where real-time issues, concurrency, fault tolerance and distributed computing are required features. On this way, Tsung uses the <em>Erlang</em> lightweight processes to simulate each hipothetical user, and that's why Tsung is able to "create" a so impressive amount of simultaneous users from a single CPU.

Another interesting feature is that, since <em>Erlang </em>was designed for distributed environments, Tsung is designed to take advantage of this when designing the <em>"stressing architecture"</em>  for your server: you can have only a client stressing a server, of course, but you also have the chance of having a cluster of <em>Erlang</em> nodes working together for being able to stress <strong>even more</strong> the "defenceless" server. And that's the reason I wrote this post: today I was benchmarking an application I started some time ago, and I was really impressed by the way Tsung manages this task... and the ease of getting it working just from downloading the sources from <a target="_blank" title="Tsung" href="http://tsung.erlang-projects.org/">its web site</a>.

Unfortunately, documentation about Tsung it's not too much (but enough), so might be you spend some time trying to understand how you can configure it, and how to use it... but, when you already know that issues, it's so easy to use it and so impressive to see the results... especially if you are stressing an application running over the <a target="_blank" title="Yaws - Yet Another Web Server" href="http://yaws.hyber.org">yaws web server</a>, which is also developed using <em>Erlang</em> and is able to work with lots of simultaneous requests, as you can see <a title="Apache VS Yaws" target="_blank" href="http://www.sics.se/~joe/apachevsyaws.html">here.</a>

In conclusion, if you are currently looking for a tool to test your server, I'd suggest you to take a look into the <a target="_blank" title="Tsung" href="http://tsung.erlang-projects.org/">Tsung web site</a> and give it a try... especially if you have several computers connected through a LAN, and you can use them as a <em>"stressing cluster"</em>. I think you'll like it.

Enjoy it!
