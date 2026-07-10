---
title: The new baobab widget
date: '2006-07-19T19:13:59+00:00'
slug: the-new-baobab-widget
categories:
- GNOME
- Planet GNOME
- Planet Igalia
wp_id: 249
---

As many of you ("igalians") already know, some time ago we[*] started working in the development of a new widget for a gnome application called <a title="Baobab" href="http://www.marzocca.net/linux/baobab.html" target="_blank">baobab</a>. The main motivation for us to work on this task was being able to get a better graphical view of the disk space usage information retrieved by the original baobab program, in a similar way as done by the <a title="KDE's filelight" href="http://www.kde-apps.org/content/show.php?content=9887" target="_blank">KDE's filelight</a> application. This KDE app shows such that disk usage as a beautiful ringchart (which offers a very good idea about the size of scanned dirs), instead of just using a treeview with one scanned dir by row, which is not so visually impressive as in the filelight's ringchart.

However, you could notice that baobab already has got a graphical representation (apart from the treeview), which shows the disk usage as a colored treemap as described on <a title="Treemap description" href="http://www.cs.umd.edu/hcil/treemap-history/index.shtml" target="_blank">this web page</a> from the University of Maryland. I'd like to say here that this is a very good visual representation for the disk usage too, but I think that is not so "practical" and <span style="cursor: pointer">understandable </span>as the ringchart one... and that's why we began to work in this issue.

Nowadays, we've currently developed an alpha version for this new widget and have sent source code and an screenshot to baobab's main developers to see what they think about it. As a result, since first feedbacks seemed to be good enough for us, we expect this contrib could be added to the original baobab in a near future :) if we keep ourselves working in it.

Meanwhile, you can take a look into our work by watching the following <strong>screenshot</strong>:

<a title="Baobab ringchart in action!" href="/wp-content/uploads/2006/07/baobab-ringchart.png" target="_blank"><img src="/wp-content/uploads/2006/07/baobab-ringchart.png" alt="Baobab ringchart in action!" align="middle" /></a>

[*] :: <a title="Alex's blog" href="https://blogs.igalia.com/alex" target="_blank">Alex</a>, <a title="Miguel's web" href="http://personales.igalia.com/magomez" target="_blank">Miguel</a>, <a title="Alejandro Piñeiro's web" href="http://personales.igalia.com/apinheiro" target="_blank">A.Piñeiro</a>, Henrique and I.
