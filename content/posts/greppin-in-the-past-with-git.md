---
title: Greppin' in the past with git
date: '2013-11-14T00:25:35+00:00'
slug: greppin-in-the-past-with-git
categories:
- Git
- Planet GNOME
- Planet GPUL
- Planet WebKitGTK
- Planeta GNOME Hispano
- Tips
- WebKit
wp_id: 1641
---

It seems that one can never stop learning new things with <em>git</em>, no matter for how long you've been using it (in my case, I'm a <em>proud git user</em> since 2008), because today I added a new trick to my toolbox, that already proved to be quite useful: "grepping" files in a git repository, as you would do it with <em>git grep, </em>but using a <em>commit-id</em> to limit the search to a specific snapshot of your project.

In other words, I found that it's possible to do things like, say, grep files to search for something in your repository considering how it was, say, some commits ago.

This is the "magical" command:

&nbsp;&nbsp;&nbsp;&nbsp;git grep <strong>&lt;search-params&gt;</strong> <strong>&lt;tree-id&gt;</strong>

This is what I get if I try to search for <em>updateBackingStore()</em> in my local clone of <a title="WebKit" href="http://www.webkit.org">WebKit</a>, as if my current branch was "50 commits older" than what it actually is:
<pre>$ git grep updateBackingStore HEAD~50
0ae236137d560da6ca889a826a8f3d023364a669:AccessibilityObject.cpp:void AccessibilityObject::updateBackingStore()
0ae236137d560da6ca889a826a8f3d023364a669:AccessibilityObject.h:    void updateBackingStore();
0ae236137d560da6ca889a826a8f3d023364a669:AccessibilityObject.h:inline void AccessibilityObject::updateBackingStore() { }
0ae236137d560da6ca889a826a8f3d023364a669:atk/WebKitAccessibleUtil.h:        coreObject-&gt;updateBackingStore(); \
0ae236137d560da6ca889a826a8f3d023364a669:atk/WebKitAccessibleUtil.h:        coreObject-&gt;updateBackingStore(); \
0ae236137d560da6ca889a826a8f3d023364a669:atk/WebKitAccessibleWrapperAtk.cpp:    coreObject-&gt;updateBackingStore();
0ae236137d560da6ca889a826a8f3d023364a669:ios/WebAccessibilityObjectWrapperIOS.mm:    m_object-&gt;updateBackingStore();
0ae236137d560da6ca889a826a8f3d023364a669:ios/WebAccessibilityObjectWrapperIOS.mm:    m_object-&gt;updateBackingStore();
0ae236137d560da6ca889a826a8f3d023364a669:mac/WebAccessibilityObjectWrapperBase.mm:    // Calling updateBackingStore() can invalidate this element so self must be retained.
0ae236137d560da6ca889a826a8f3d023364a669:mac/WebAccessibilityObjectWrapperBase.mm:    m_object-&gt;updateBackingStore();</pre>
I don't know about you, but I find this quite useful for me to answer questions such as "Where was this function being used in commit X?", and things like that.

Anyway, you might have noticed that I mentioned <strong>&lt;tree-id&gt;</strong> in the recipe instead of <strong>&lt;commit-id&gt;</strong>, yet I used <em>HEAD~50 </em>in the example, which is actually a <em>commit-id.</em> And still works.

And the short explanation, without trying to explain here all the different kind of data types that git keeps internally for every repository (mainly <em>commits</em>, <em>trees</em> and <em>blobs</em>), is that git is smart enough to find the right <em>tree-id</em> associated to a given <em>commit-id</em> by just considering <strong>the current path </strong>inside the repository and the <strong>tree-id associated to the top directory for a given commit</strong>.

But how to know that <em>tree-id</em> myself in case I want to? Easy, just <em>pretty print</em> the full information of the <em>commit</em> object you're interested in, instead of only seeing the abbreviated version (what you usually see with git show or git log:
<pre>$ git cat-file -p HEAD~50
tree 0ae236137d560da6ca889a826a8f3d023364a669
parent bdb7a7949a29988da3fe50a65d6c694d5084d379
author [...]</pre>
See that <em>tree </em>thing in the first line? That's the <em>tree-id</em> that git needs for grepping, which as you can see can be easily extracted from a particular commit. Actually, you could get easily the <em>tree-id</em> for any subdirectory from this point, by using the <em>git ls-tree</em> command:
<pre>$ git ls-tree 0ae236137d560da6ca889a826a8f3d023364a669
100644 blob 3fe2340c9614e893f0dfeb720f23773bbf1ea076	.dir-locals.el
100644 blob 741c4d53b5a0338cf36900a283e89408d0f9d457	.gitattributes
100644 blob f45a975762be9a429aa971c18da01b433c559553	.gitignore
100644 blob d571aa28ea86c14c7880533bf3ba68e9ef4b3c81	.qmake.conf
100644 blob 10f85055ae9f3823f0d20808599f644c18af7921	CMakeLists.txt
100644 blob 5eb66e7bcbc7543eb3a4dbf183a9043545776659	ChangeLog
100644 blob 7dbe9d2e0029bab47b8b2b22065a1032ecfe4434	ChangeLog-2012-05-22
040000 tree d42a0b3121ed7993cfd250426d20472769760f87	Examples
100644 blob 78d89e5c70ad56c38b0c25e7705d42fa380c4ee0	GNUmakefile.am
040000 tree 4a9e87fc1f35efa1349a18b1df694530c981c57e	LayoutTests
100644 blob 14e33157011157797dac62c494bac0bf254d7c2f	Makefile
100644 blob ee723d830dea51d1ce9e2d1ad8c985eeca2d4f3f	Makefile.shared
040000 tree 20c763d6a4e8749ad9e041e8372e9f47dc722f45	ManualTests
040000 tree 660d88b926cf618ab9e1612b8e2a3e97b15dbcbe	PerformanceTests
040000 tree fbf9703d3e9a9e4cf2ff10817c99ba3a5de87410	Source
040000 tree 346110c441a674334f5f56ef42b9dd40def89c76	Tools
040000 tree 262cb11d9b491be35daee570f9b825bce5715579	WebKit.xcworkspace
040000 tree b9e48a7a24b4973b253ee14053808b40d67c94aa	WebKitLibraries
040000 tree adce37b690957abdd21d2dd8ff77302c5a5a9071	Websites
100755 blob befd429487fc5ac9bb3494800f4eeaef1e607663	autogen.sh</pre>
And of course, "navigating" with more calls to <em>git ls-tree </em>you could also get the <em>tree-id</em> for a specific subdirectory, in case you wanted to constraint the search to that specific path of your repo.

However, considering that git is so good at translating a <em>commit-id </em>into a <em>tree-id</em>, my personal recommendation is that, instead, you first <em>cd </em>into the path you want to focus the search in, and then let <em>git </em> do its "magic" by just using the <em>git grep &lt;search-params&gt; &lt;tree-id&gt;<strong> </strong></em>command.

So that's it. Hope you find this useful, and please do not hesitate to share any comment or suggestion you might have with regard to this or any other "git trick" you might know.

I honestly love using git so much that sometimes I wonder if coding is not just a poor excuse to use git. Probably not, but the thing is that I can not imagine my life without it anymore. That's a fact.
