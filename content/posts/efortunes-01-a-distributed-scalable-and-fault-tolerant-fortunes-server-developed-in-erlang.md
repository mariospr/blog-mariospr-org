---
title: 'eFortunes 0.1: a distributed, scalable and fault-tolerant fortunes server developed in Erlang'
date: '2006-11-02T21:08:53+00:00'
slug: efortunes-01-a-distributed-scalable-and-fault-tolerant-fortunes-server-developed-in-erlang
categories:
- Erlang
- Planet GPUL
- Planet Igalia
- Yaws
wp_id: 13
---

Well, after naming this post in this way I think it could be a good idea to explain what this is about... :)

As the result of working in my Master Thesis, I developed an small "ad-hoc" framework for programming simple and so-so-small web applications using <a title="Erlang" href="http://www.erlang.org/" target="_blank">Erlang</a>, since a requirement for doing my Thesis was using distributed functional technology... and web applications are not usually developed with this kind of tools. Well, I know that with <a title="ErlyWeb: The Erlang Twist on Web Frameworks" href="http://erlyweb.org/" target="_blank">ErlyWeb</a> this assertion could be wrong in a matter of months ;), but when I started my work (a year ago) the situation was so much different from now.

In the other hand, my fellow worker <a title="Javier Muñoz's blog" href="https://blogs.igalia.com/jmunhoz" target="_blank">Javier Muñoz</a> had recently developed a so much practical script ("Erlang On Rails", as he called it) for easily start with the development of Erlang applications, without getting lost (and bored) with several commonly needed issues, such as the application definition file, the compilation process or the launcher script. <a title="erlang on rails" href="https://blogs.igalia.com/jmunhoz/2006/10/18/erlang-on-rails/" target="_blank">On this post</a> you can read more about "Erlang On Rails", as it was told by Javi some days ago.

With this background on mind, I felt myself encouraged to develop an small web application that let me to carry on learning about the Erlang world, now that my Thesis is (at last) over... and I thinked about doing an "absurd" (well, this is subjective :)) fortunes server could be a good choice, since I could learn with it more about so many issues about Erlang I haven't learnt yet, or get a deeper knowledge about issues I've already know. For instance:
<ul>
	<li>Distributed persistence of data (fortunes) using <a title="Mnesia: a distributed DataBase Management System" href="http://erlang.org/doc/doc-5.5.1/lib/mnesia-4.3.2/doc/html/index.html" target="_blank">Mnesia</a>, a Erlang-based objectual DBMS.</li>
	<li>Persistence into a relational DBMS (such as <a title="PostgreSQL: The world's most advanced open source database" href="http://www.postgresql.org/" target="_blank">PostgreSQL</a>) using the ODBC API provided by the <a title="Erlang" href="http://www.erlang.org/" target="_blank">Erlang/OTP</a> platform. (Nowadays, it seems Mnesia is not suitable for storing large amounts of data)</li>
	<li>Developing reliable and fault-tolerance applications on Erlang according the design principles of the supervision tree, as suggested on the Erlang/OTP documentation at erlang.org. (Well, sometimes fortunes are a really-critical information... don't you think?)</li>
	<li>Designing of web applications with Erlang using <a title="Yet Another Web Server" href="http://yaws.hyber.org" target="_blank">Yaws</a>, a light web server developed on Erlang which is quickly growing on these days, adding more and more capabilities with each version that is out (such as <a title="Asynchronous JavaScript and XML" href="http://en.wikipedia.org/wiki/AJAX" target="_blank">AJAX</a> or <a title="haXe: web oriented universal language" href="http://haxe.org/" target="_blank">haXe</a> support).</li>
	<li>Testing several frameworks I've recently discovered on the web, and that I wasn't able on my Thesis because of a matter of time: <a title="Yet Another Test Server (yaws compatible)" href="http://code.google.com/p/yatsy/" target="_blank">Yatsy</a>, <a title="ErlyDB: The Erlang Twist on Database Abstraction" href="http://code.google.com/p/erlydb/" target="_blank">ErlyDB</a>, <a title="A Simple Erlang Template Language" href="http://code.google.com/p/erltl/" target="_blank">ErlTL</a>, <a title="ErlyWeb: The Erlang Twist on Web Frameworks" href="http://code.google.com/p/erlyweb/" target="_blank">ErlyWeb</a>...</li>
	<li>And so on...</li>
</ul>
In fact, all these points could be abbreviated as "learning more about Erlang and having an workbench for testing all those issues I'd like". And if, while learning in this way, I get a distributed, scalable and fault-tolerant fortunes server for being able to safely store jokes and spontaneus comments... "better than better" XD

At last, I'd like to thank my Master Thesis's director (<a title="Víctor M. Gulías Home Page" href="http://www.dc.fi.udc.es/~gulias/" target="_blank">Víctor M. Gulías</a>) for letting me to license my work under the terms of the <a title="GNU General Public License" href="http://www.gnu.org/copyleft/gpl.html" target="_blank">GNU General Public License</a>, in order to let everyone to get the source of eFortunes and use it as needed.

Now I'll end this post by telling the current features of eFortunes 0.1, the TODO list (this one could change, of course) for eFortunes 0.2 and some screenshots of it. And, of course... you can <strong>download the source code</strong> if you want from here:

<a title="eFortunes 0.1 source code" href="/sources/efortunes/efortunes-0.1.tar.gz">efortunes-0.1.tar.gz</a>

<strong>eFortunes 0.1 features:</strong>
<ul>
	<li>List, create, edit or remove fortunes from server</li>
	<li>Underlying distributed persistence layer based on the Mnesia DBMS</li>
	<li>Easy access to the services offered by efortunes by using a simple web interface (powered by yaws)</li>
	<li>Internationalization (i18n) support for the implementation of the web interface</li>
</ul>
<strong>eFortunes 0.2 TODO list:</strong>
<ul>
	<li>Bug fixing ;)</li>
	<li>Add the capability of importing/exporting from/to regular fortunes files</li>
	<li>Add search interface for making possible to look for fortunes according some specific criteria</li>
	<li>Improve the web interface ( well... this is a must ;) )</li>
	<li>Add an user profiles management tool (currently, only an user admin/admin exists)</li>
	<li>Create an standalone, deployable daemon of efortunes (maybe, yaws should be embedded into an erlang application)</li>
	<li>Documentation and code-cleaning</li>
</ul>
<strong>eFortunes screenshots</strong> (sorry, only spanish text on them):
<p align="center"><a title="List all the fortunes" href="/wp-content/uploads/2006/11/listAllFortunes.png" target="_blank"><img src="/wp-content/uploads/2006/11/listAllFortunes_thumb.png" alt="List all the fortunes" /></a></p>
<p align="center"><a title="Edit a fortune" href="/wp-content/uploads/2006/11/editFortune.png" target="_blank"><img src="/wp-content/uploads/2006/11/editFortune_thumb.png" alt="Edit a fortune" /></a> <a title="Deployment of eFortunes" href="/wp-content/uploads/2006/11/eFortunesDeployment.png" target="_blank"><img src="/wp-content/uploads/2006/11/eFortunesDeployment_thumb.png" alt="Deployment of eFortunes" /></a></p>
