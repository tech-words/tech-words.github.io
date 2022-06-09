Rails refers to itself as "opinionated software", but it might also be termed "arrogant software".

It states:

    If you learn �The Rails Way� you�ll probably discover a tremendous increase in productivity. If you persist in bringing old habits from other languages to your Rails development, and trying to use patterns you learned elsewhere, you may have a less happy experience.

And quotes 3 over-arching philosophies:

 * DRY
 * Convention Over Configuration
 * REST best practice

These are all principles I agree with. The guide states that in many cases there *is* one best way to solve a problem, and Rails will point you to that method, and in some cases actively prevent you following a "lesser" method. To an extent, this opinionated position is necessary for the "convention over configuration" method - because it decides on that convention.

This obviously is an arrogant position. Rails thinks that it knows better than you do what the best way to solve a problem is. The real strength of Rails (as with Ruby) is that they have a very active community of experience developers, so the framework stays fairly up-to-date and the normally do know what they're talking about. However, this position still falls down for two reasons:

 1. Rails as a framework cannot always be completely up-to-the-minute with the latest thinking in best-practice.
 2. Sometimes, they're just wrong.

So, to the examples.

Bad citizen
---

My first allegation against rails is that they are a bad citizen of the web. There are established and accepted technologies for client-side scripting and markup - HTML(5) and JavaScript - but the Rails (or Ruby?) community in its arrogance believes it can improve on both of them. Rails developers are encouraged to write Coffee Script to compile into JavaScript, and HAML to compile into HTML. This is really really annoying for a number of reasons:

 - You can't share code with other systems without converting it first.
 - By server-side compiling all your client-side code you blur the lines between client- and server-side.
 - You can't use any updates to HTML or JavaScript until the updates are incorporated into HAML or Coffee.
 - In the case of Coffee, it's not even a perfect super-set of JavaScript - valid JavaScript is invalid Coffee script. Why?

The most important point, that makes them a bad citizen, is the first one. Instead of all developers writing client-side scripting in JavaScript, now there's a whole codebase building up of Coffee. People post Coffee into Stack Overflow questions. So now there are two unrelated languages that we all need to solve JavaScript problems in, instead of one. That's confusing for everyone.

Bad practice
---

My second beef against Rails is this: To justify their "opinionated" position they must at least come close to promoting best practice in all the functions of the framework. While they do adhere well to the best practices they explicitly list (DRY, convention over configuration and REST) they fall down in the of the more nuanced architectural points.

* Active Record *

Rails encourages all models to extend from its ActiveRecord class. Don't get me wrong, it's a very solid implementation of Active Record. The problem is that Active Record has been considered quite a harmful anti-pattern for a number of years. Inherently linking the models in your code to your database architecture is a *terrible* idea for the flexibility of your application.

If you now want to swap out a database for a web service, or change the underlying data structure without breaking your application, or add some pre-processing on your data before it's exposed to your app, you're kinda screwed. You just have to extend ActiveRecord and then replace all your models that extend from ActiveRecord to extend from a new class instead = ball-ache.

Which could be rephrased as:

    If you have any opinions of your own, you're in for a world of hell.

These I cannot fault.
