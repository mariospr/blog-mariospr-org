---
title: The Web Platform Tests project
date: '2020-05-14T09:07:19+00:00'
slug: the-web-platform-tests-project
categories:
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planeta GNOME Hispano
- Chromium
- Web Platform Tests
- Testing
- Web Browsers
wp_id: 2961
aliases:
- /2020/05/13/the-web-platform-tests-project/
---

<h2>Web Browsers and Test Driven Development</h2>
Working on Web browsers development is not an easy feat but if there's something I'm personally very grateful for when it comes to collaborating with this kind of software projects, it is their testing infrastructure and the peace of mind that it provides me with when making changes on a daily basis.

To help you understand the size of these projects, they involve millions of lines of code (<a href="https://www.openhub.net/p/chrome" target="_blank" rel="nofollow noreferrer noopener">Chromium is ~25 million lines of code</a>, followed closely by <a href="https://www.openhub.net/p/firefox" target="_blank" rel="nofollow noreferrer noopener">Firefox</a> and <a href="https://www.openhub.net/p/webkit" target="_blank" rel="nofollow noreferrer noopener">WebKit</a>) and around 200-300 new patches landing everyday. Try to imagine, for one second, how we could make changes if we didn't have such testing infrastructure. It would basically be utter and complete chao​s and, more especially, it would mean extremely buggy Web browsers, broken implementations of the <a href="https://webplatform.github.io" target="_blank" rel="nofollow noreferrer noopener">Web Platform</a> and tens (hundreds?) of new bugs and crashes piling up every day... not a good thing at all for Web browsers, which are these days some of the most widely used applications (and not just 'the thing you use to browse the Web').
<p style="text-align: center;"><a href="https://i1.wp.com/mariospr.org/wp-content/uploads/2020/05/ChromiumTrybots.png"><img src="https://i1.wp.com/mariospr.org/wp-content/uploads/2020/05/ChromiumTrybots.png" alt="The Chromium Trybots in action" /></a>
<small><em>The Chromium Trybots in action</em></small></p>
Now, there are all different types of tests that Web engines run automatically on a regular basis: Unit tests for checking that APIs work as expected, platform-specific tests to make sure that your software runs correctly in different environments, performance tests to help browsers keep being fast and without increasing too much their memory footprint... and then, of course, there are the tests to make sure that the Web engines at the core of these projects implement the Web Platform correctly according to the numerous standards and specifications available.

And it's here where I would like to bring your attention with this post because, when it comes to these last kind of tests (what we call "Web tests" or "layout tests"), each Web engine used to rely entirely on their own set of Web tests to make sure that they implemented the many different specifications correctly.

Clearly, there was some room for improvement here. It would be wonderful if we could have an engine-independent set of tests to test that a given implementation of the Web Platform works as expected, wouldn't it? We could use that across different engines to make sure not only that they work as expected, but also that they also behave <strong>exactly</strong> in the same way, and therefore give Web developers confidence on that they can rely on the different specifications without having to implement engine-specific quirks.
<h2><a id="user-content-enter-the-web-platform-tests-project" class="anchor" href="#enter-the-web-platform-tests-project" aria-hidden="true"></a>Enter the Web Platform Tests project</h2>
Good news is that just such an ideal thing exists. It's called the <a href="https://web-platform-tests.org/index.html" target="_blank" rel="nofollow noreferrer noopener">Web Platform Tests project</a>. As it is concisely described in <a href="https://web-platform-tests.org/index.html" target="_blank" rel="nofollow noreferrer noopener">it's official site</a>:

<em>"The web-platform-tests project is a cross-browser test suite for the Web-platform stack. Writing tests in a way that allows them to be run in all browsers gives browser projects confidence that they are shipping software which is compatible with other implementations, and that later implementations will be compatible with their implementations."</em>

I'd recommend visiting <a href="https://web-platform-tests.org/index.html">its website</a> if you're interested in the topic, watching the <a href="https://www.youtube.com/watch?v=zuK1uyXPZS0"><em>"Introduction to the web-platform-tests"</em> video</a> or even glance at <a href="https://github.com/web-platform-tests/wpt" target="_blank" rel="nofollow noreferrer noopener">the git repository containing all the tests here</a>. Here, you can also find specific information such as <a href="https://web-platform-tests.org/running-tests/index.html" target="_blank" rel="nofollow noreferrer noopener">how to run WPTs</a> or <a href="https://web-platform-tests.org/writing-tests/index.html" target="_blank" rel="nofollow noreferrer noopener">how to write them</a>. Also, you can have a look as well at the <a href="https://wpt.fyi" target="_blank" rel="nofollow noreferrer noopener">wpt.fyi dashboard</a> to get a sense of what tests exists and how some of the main browsers are doing.
<p style="text-align: center;"><iframe src="https://www.youtube.com/embed/zuK1uyXPZS0" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe></p>
In short: I think it would be safe to say that <strong>this project is critical to the health of the whole Web Platform</strong>, and ultimately to Web developers. What's very, very surprising is how long it took to get to where it is, since it came into being only about <a href="https://www.w3.org/blog/2013/02/testing-the-open-web-platform/" target="_blank" rel="nofollow noreferrer noopener">halfway into the history of the Web</a> (there were <a href="https://lists.w3.org/Archives/Public/public-css-testsuite/2004Mar/0001.html">earlier testing efforts at the W3C</a>, but none that focused on automated &amp; shared testing). But regardless of that, this is an interesting challenge: Filling in all of the missing unified tests, while new things are being added all the time!

Luckily, this was a challenge that did indeed took off and all the major Web engines can now proudly say that they are <strong>regularly running about 36500 of these Web engine-independent tests</strong> (providing <strong>~1.7 million sub-tests</strong> in total), and all the engines are showing off a <strong>pass rate between 91% and 98%</strong>. See the numbers below, as extracted from <a href="https://wpt.fyi/">today's WPT data</a>:
<table border="0" cellspacing="0">
<tbody>
<tr>
<td style="text-align: center; padding: 2px;" colspan="2" valign="middle" height="17"><b>Chrome 84</b></td>
<td style="text-align: center; padding: 2px;" colspan="2" valign="middle"><b>Edge 84</b></td>
<td style="text-align: center; padding: 2px;" colspan="2" valign="middle"><b>Firefox 78</b></td>
<td style="text-align: center; padding: 2px;" colspan="2" valign="middle"><b>Safari 105 preview</b></td>
</tr>
<tr>
<td style="text-align: center; padding: 2px;" height="17"><b>Pass</b></td>
<td style="text-align: center; padding: 2px;"><b>Total</b></td>
<td style="text-align: center; padding: 2px;"><b>Pass</b></td>
<td style="text-align: center; padding: 2px;"><b>Total</b></td>
<td style="text-align: center; padding: 2px;"><b>Pass</b></td>
<td style="text-align: center; padding: 2px;"><b>Total</b></td>
<td style="text-align: center; padding: 2px;"><b>Pass</b></td>
<td style="text-align: center; padding: 2px;"><b>Total</b></td>
</tr>
<tr>
<td style="text-align: center; padding: 2px;" valign="middle" height="17">1680105</td>
<td style="text-align: center; padding: 2px;">1714711</td>
<td style="text-align: center; padding: 2px;" valign="middle">1669977</td>
<td style="text-align: center; padding: 2px;">1714195</td>
<td style="text-align: center; padding: 2px;" valign="middle">1640985</td>
<td style="text-align: center; padding: 2px;">1698418</td>
<td style="text-align: center; padding: 2px;" valign="middle">1543625</td>
<td style="text-align: center; padding: 2px;">1695743</td>
</tr>
<tr>
<td style="text-align: center; padding: 2px;" colspan="2" valign="middle" height="17"><b>Pass rate: 97.98%</b></td>
<td style="text-align: center; padding: 2px;" colspan="2" valign="middle"><b>Pass rate: 97.42%</b></td>
<td style="text-align: center; padding: 2px;" colspan="2" valign="middle"><b>Pass rate: 96.62%</b></td>
<td style="text-align: center; padding: 2px;" colspan="2" valign="middle"><b>Pass rate: 91.03%</b></td>
</tr>
</tbody>
</table>
And here at <a href="http://www.igalia.com">Igalia</a>, we've recently had the opportunity to work on this for a little while and so I'd like to write a bit about that...
<h2><a id="user-content-the-web-platform-project-and-the-coronavirus-outbreak" class="anchor" href="#the-web-platform-project-and-the-coronavirus-outbreak" aria-hidden="true"></a>Upstreaming Chromium's tests during the Coronavirus Outbreak</h2>
As you all know, we're in the middle of an unprecedented world-wide crisis that is affecting everyone in one way or another. One particular consequence of it in the context of the Chromium project is that <a href="https://blog.chromium.org/2020/03/upcoming-chrome-releases.html" target="_blank" rel="nofollow noreferrer noopener">Chromium releases were paused for a while</a>. On top of this, some <a href="https://groups.google.com/a/chromium.org/d/msg/chromium-dev/Vn7uzglqLz0/6oGsNFUZEAAJ" target="_blank" rel="nofollow noreferrer noopener">constraints on what could be landed upstream were put in place</a> to guarantee quality and stability of the Chromium platform during this strange period we're going through these days.

These particular constraints impacted my team in that we couldn't really keep working on the tasks we were working on up to that point, in the context of <a href="http://www.chromium.org">the Chromium project</a>. Our involvement with the <a href="https://docs.google.com/document/d/1lzGeXN4nwnANdFSpVxmJ1TUgb3QBPFCjVxLsFVBlKdE/edit#heading=h.uokewwiwnmn" target="_blank" rel="nofollow noreferrer noopener">Blink Onion Soup 2.0 project</a> usually requires the landing of relatively large refactors, and these kind of changes were forbidden for the time being.

Fortunately, we found an opportunity to collaborate in the meantime with the Web Platform Tests project by <strong>analyzing and trying to upstream many of the existing Chromium-specific tests</strong> that haven't yet been unified. This is important because tests exist for widely used specifications, but if they aren't in Web Platform Tests, their utility and benefits are limited to Chromium. If done well, this would mean that all of the tests that we managed to upstream would be immediately available for everyone else too. Firefox and WebKit-based browsers would not only be able to identify missing features and bugs, but also be provided with an extra set of tests to check that they were implementing these features correctly, and interoperably.
<p style="text-align: center;"><a href="https://i0.wp.com/mariospr.org/wp-content/uploads/2020/05/WPTDashboard.png"><img src="https://i0.wp.com/mariospr.org/wp-content/uploads/2020/05/WPTDashboard.png" alt="The WPT Dashboard" /></a>
<small><em>The WPT Dashboard</em></small></p>
It was an interesting challenge considering that we had to switch very quickly from writing <em>C++</em> code around the <a href="https://www.chromium.org/developers/design-documents/inter-process-communication">IPC layers of Chromium</a> to analyzing, migrating and upstreaming Web tests from the huge pool of Chromium tests. We focused mainly on <a href="https://drafts.csswg.org/css-grid-2/">CSS Grid Layout</a>, <a href="https://drafts.csswg.org/css-flexbox-1/">Flexbox</a>, <a href="https://drafts.fxtf.org/css-masking-1/">Masking</a> and <a href="https://drafts.fxtf.org/filter-effects">Filters</a> related tests... but I think the results were quite good in the end:

As of today, I'm happy to report that, during the ~<strong>4 weeks we worked on this</strong> my team <strong><a href="https://docs.google.com/spreadsheets/u/2/d/1Fw1YRl9S8WNUkwwaFXZ0MCE0Qi3RcOJPPJm2tWhz6xw">migrated 240 Chromium-specific Web tests</a> to the Web Platform Tests' upstream repository</strong>, helping increase test coverage in other Web Engines and thus helping towards improving interoperability among browsers:
<ul>
 	<li><strong>CSS Flexbox</strong>: 89 tests migrated</li>
 	<li><strong>CSS Filters</strong>: 44 tests migrated</li>
 	<li><strong>CSS Masking</strong>: 13 tests migrated</li>
 	<li><strong>CSS Grid Layout</strong>: 94 tests migrated</li>
</ul>
But there is more to this than just numbers. Ultimately, as I said before, these migrations should help <strong>identifying missing features and bugs</strong> in other Web engines, and that was precisely the case here. You can easily see this by checking the <strong><a href="https://bugzilla.mozilla.org/buglist.cgi?bug_status=UNCONFIRMED&amp;bug_status=NEW&amp;bug_status=ASSIGNED&amp;bug_status=REOPENED&amp;bug_status=RESOLVED&amp;bug_status=VERIFIED&amp;bug_status=CLOSED&amp;chfieldto=2020-04-25&amp;chfield=%5BBug%20creation%5D&amp;resolution=---&amp;resolution=FIXED&amp;resolution=INVALID&amp;resolution=WONTFIX&amp;resolution=INACTIVE&amp;resolution=DUPLICATE&amp;resolution=WORKSFORME&amp;resolution=INCOMPLETE&amp;resolution=SUPPORT&amp;resolution=EXPIRED&amp;resolution=MOVED&amp;chfieldfrom=2020-03-22&amp;order=Last%20Updated&amp;query_format=advanced&amp;short_desc=wpt%20new%20failures%20css&amp;short_desc_type=allwordssubstr&amp;classification=Components&amp;product=Core">list of automatically created bugs in Firefox's bugzilla</a></strong>, as well as <a href="https://bugs.webkit.org/show_bug.cgi?id=210091">some</a> <a href="https://bugs.webkit.org/show_bug.cgi?id=210586">of</a> <a href="https://bugs.webkit.org/show_bug.cgi?id=210587">the</a> <a href="https://bugs.webkit.org/show_bug.cgi?id=209983">bugs</a> filed in <strong><a href="https://bugs.webkit.org/">WebKit's bugzilla</a></strong> during the time we worked on this.

...and note that this doesn't even include the additional <strong>96 Chromium-specific tests that we analyzed but determined were not yet eligible</strong> for migrating to WPT (normally because they relied on some internal Chromium API or non-standard behaviour), which would require further work to get them upstreamed. But that was a bit out of scope for those few weeks we could work on this, so we decided to focus on upstreaming the rest of tests instead.

Personally, I think this was a big win for the Web Platform and I'm very proud and happy to have had an opportunity to have contributed to it during these dark times we're living, as part of my job at <a href="http://www.igalia.com">Igalia</a>. Now I'm back to working on the <a href="https://docs.google.com/document/d/1lzGeXN4nwnANdFSpVxmJ1TUgb3QBPFCjVxLsFVBlKdE/edit#heading=h.uokewwiwnmn" target="_blank" rel="nofollow noreferrer noopener">Blink Onion Soup 2.0 project</a>, where I think I should write about too, but that's a topic for a different blog post.
<h2><a id="user-content-credit-where-credit-is-due" class="anchor" href="#credit-where-credit-is-due" aria-hidden="true"></a>Credit where credit is due</h2>
<a href="https://www.igalia.com"><img src="https://i2.wp.com/mariospr.org/wp-content/uploads/2020/05/IgaliaLogoSmall.png" alt="Igalia" align="right" /></a>I wouldn't want to finish off this blog post without acknowledging all the different contributors who tirelessly worked on this effort to help improve the Web Platform by providing the WPT project with these many tests more, so here it is:

From the <a href="http://www.igalia.com">Igalia</a> side, my whole team was the one which took on this challenge, that is: Abhijeet, Antonio, Gyuyoung, Henrique, Julie, Shin and myself. Kudos everyone!

And from the reviewing side, many people chimed in but I'd like to thank in particular the following persons, who were deeply involved with the whole effort from beginning to end regardless of their affiliation: Christian Biesinger, David Grogan, Robert Ma, Stephen Chenney, Fredrik Söderquist, Manuel Rego Casasnovas and Javier Fernandez. Many thanks to all of you!

Take care and stay safe!
