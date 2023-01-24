# No more thinking of names for style classes

## 1\. No more thinking of names for style classes

When you use traditional ways to style, you have to think about what kinds of content and styles you might have and then try to make classes that let you apply these styles. Or you have base styles that usually work but need to be overridden occasionally. This can get quite overwhelming, begging questions like:

* Will I use this more than once?
    
* If I use this again, will it need to be a bit different in some way?
    
* What naming conventions do I use?
    
* Should I name this after the appearance, the function, or something else?
    
* What conventions should I use to name and organize my CSS?
    

Naming might not sound all that challenging, but considering all of the above, try to be consistent about it over time and across team members. It is actually *very* difficult! A lot of mental work is done, and this often leads to "bike shedding," which is when people on a team argue about what things should be called.

When using Tailwind CSS, there’s far less of a need to name classes, as you just apply the utility classes specified in the documentation. Once you start using Tailwind, most of the class names become fairly intuitive, and lesser-used ones are easily looked up in [Tailwind’s excellent documentation](https://tailwindcss.com/).

## 2\. Much less switching contexts between CSS files/style blocks and HTML code

Normally when you’re writing your core webpage structure, you’ll be writing HTML and JS, and often think things like

* “I just need to add some margin to this”.
    
* “This text needs to be bigger.”
    
* “I have to make a class for this new type of element.”
    

Every time you do that, you have likely needed to either switch to another tab of your IDE with your CSS or scroll all the way up to the top of your document head, where you’ve got a `<style>` block.

Whenever you do this, you have this context switching and have to spend time moving around, making the change to your CSS, and then getting back into the document.

When you use Tailwind CSS, usually you are styling things inline, right in your CSS in the class attributes, so you don’t have to switch to this other section of your code. That makes you so much faster. If you’re already experienced enough that you’re used to working the former way, you probably don’t even realize how much time you’re spending switching between documents and finding your place, but this is a tremendous benefit to the utility-first approach to working with CSS.

## 3\. You can use variants with media queries, pseudo-classes, and child-selectors

Inline styles cannot use media queries. For instance, if you want an element to display one way on small screens and another way on large screens, you would normally need to create different sets of selectors in different parts of your CSS. This can be quite cumbersome because you have to find multiple sections of your stylesheet and edit them.

Fortunately, Tailwind allows you to do all of this kind of styling inline without having to create different selectors for each variant. Here are just a few:

* Size classes (sm, md, lg, xl)
    
* hover
    
* focus
    
* active
    
* dark mode (through either parent class or media query)
    
* first, last, odd, even
    
* form states like required, invalid, disabled
    
* group and peer to modify things in the child or adjacent elements
    
* before and after to modify pseudo-elements
    
* placeholder (for form elements that aren’t filled in)
    
* markers to style bullets in lists
    

There are a ton, and more of these variants are being added all the time. Check [the variants page on the docs](https://tailwindcss.com/docs/hover-focus-and-other-states) for a more complete list with examples.

## 4\. Tailwind helps enforce a coherent design system (without being too restrictive)

If you’ve ever tried to design a large, complex site or create a design system for a company to use, you might know that it can be tricky to enforce design decisions across a team or many pages over a long period of time.

Tailwind really helps with this because you can set up Tailwind to allow only specific values instead of having everything set to an infinite range of possible values.

* A color palette is defined with reasonable steps between shades.
    
* Spacing values are only allowed at certain intervals so spacing looks consistent. You have to choose between 12, 14, 16, 20 etc, and not every possible value, so you are less likely to end up with slightly different spacing between very similar elements.
    
* There’s a set of fonts, weights, and font sizes to use.
    
* The width breakpoints are predefined for your responsive design so you don’t have many breakpoints. (You can easily add more).
    

Of course, you can and probably will customize any of these values as required, but the point is that you don’t have to think “Hmm, do I need 18 or 19 pixels of spacing here?” or “Should this colour be #1122FF or #1128F0?”. You have a defined list of values to choose from, and this makes styling things more straightforward and consistent.

## 5\. Your production CSS only has styles you actually use

If you’ve ever maintained a massive stylesheet, you might know that over time, you might end up with a lot of cruft in there. Some styles were put in there with the expectation they’d be used a lot, but the code applied might not even exist in your codebase in time. When that happens, it can be a lot of work to look for those classes and elements and prune the unused styles from your CSS. Or worse, you just leave it in there for fear of breaking something.

In Tailwind, you’re going to be generating your CSS automatically using a build process, so your stylesheet will only have the utility classes you actually have in your code. This means that, for smaller sites, your CSS stays pretty small and compact. And for larger sites, it remains reasonable.

## 6\. Utility classes cache well

Inline styles can’t really be cached because they have to be reloaded along with the HTML content. A CSS file can be more aggressively cached, improving page load speed.

The flip-side of this is that the actual HTML may be larger with Tailwind because of all the utility classes in the content, compared to making large classes that extract the complexity out into a stylesheet. But this ends up being a pretty good tradeoff because the repetitive nature of utility classes compresses quite well at the transport layer used to transfer webpages, so the resulting difference in data transfer speeds and page load performance is extremely negligible.

## 7\. It’s easy to make style changes without overriding things

With a utility-only approach, you rarely have to worry about CSS precedence mucking things up or complicated and annoying style conflicts. If you have large style hierarchies with nested selectors, and you want to make a change, you might find yourself having to resort to using`!important`, which is rarely a good idea because it’s impossible to override that later.

Using Tailwind, your styles are usually applied directly to the thing you are styling, and if you would like to change a thing, you just change it, you don’t have to fight with higher-priority styles that have higher specificity somewhere in the chain that you have to find and contend with, like in the example below.

form.master input { padding: 8px; }

/\* Later on in the stylesheet… \*/

/\* This style will not be applied in a form with class “master” because the above has higher specificity \*/ form input { padding: 4px; }

## 8\. Extracting components helps keep code DRY

What about the repetitive nature of Tailwind? If you have a number of styled list items, for example, you seriously have to apply a long list of classes every time.

Yes and no. If you were coding a large document completely manually, this could certainly get tedious, although in those cases, modern IDEs would let you select and edit all of them simultaneously anyway. (Multi-cursor editing is an absolute godsend!) But on most useful websites, parts of a document that are used over and over again are typically made by a loop of code. So, you really only have to write such code once.

In cases where you may need to reuse a block of code, it makes more sense to extract this into reusable components in your framework (like React, Vue, or even Blade). This way, you can also combine the relevant structural HTML with all the styling for it, and have one source of truth for this bit of code that might appear on many pages.

Finally, if extracting components doesn’t make sense in your situation, you can also use Tailwind’s @apply functionality, which allows you to combine multiple Tailwind classes into a single, custom class, and combine the benefits of Tailwind with a traditional CSS approach. This can be very handy for things like buttons or form elements that are used frequently but may not have the complexity necessary to extract a component.

## 9\. Tailwind styling is so much easier to maintain!

This may be the biggest benefit of Tailwind: if you have a project using Tailwind, changing styles is very straightforward most of the time. Especially if you use styled components frequently. You simply go into your component and change the classes, or change the classes in the code you want to adjust.

In a more typical CSS environment, you might have to introduce changes to a large CSS file, and when you do this, it is not clear where exactly those styles are used, so testing and validating the changes is quite difficult and could have knock-on effects that aren’t obvious at first. Using a utility-first approach means you don’t have to dig around in a messy CSS file and hope you’re not breaking things or causing conflicts.

# Drawbacks of Tailwind

So I don't look like a Tailwind fanboy who can't stop raving about it, I'll admit that it has some problems. It’s not always perfect for all scenarios. Here are some of the major concerns.

## 1\. A build step is required

Tailwind used to be just a stylesheet that you could pull in, but in newer versions, you have to run a build process to make the CSS. This means that there’s some extra overhead to the process of creating a web page. If you’re not familiar with front-end build processes, this can add complexity that could be overwhelming to a newer developer. Fortunately, this process integrates well into the build processes used by many front-end frameworks already, and using Tailwind CLI makes it fairly easy.

## 2\. Setup and learning curve

If you already know CSS, Tailwind is another thing to learn. You have to install it, figure out how to configure it the way you want (if you can’t just accept the defaults), and then learn the conventions and class names and how different parts of Tailwind work.

Fortunately, Tailwind has excellent documentation that makes it pretty easy to find what you need, and there are many good tutorials and examples available. Usually, you only require a few days of study and practice to get pretty good at something.

## 3\. Larger HTML sizes

Because the utility-first approach often involves adding many classes to your HTML, the download size of the HTML may increase. The advantage of this is that this type of extra, repetitive data tends to compress effortlessly, so the net difference in the user experience may not be significant. Sarah Dayan from Algolia addressed this concern in her talk, “In Defense of Utility-First CSS." In it, she demonstrated the difference between a utility-first approach and a component approach with an existing page and found that the uncompressed size was about 20% larger than with the utility-first approach. But once compressed, the difference was only a few percentages.

Furthermore, the CSS document was larger than the component approach, and it ends up being a more complex document that requires more processing for the browser to traverse and apply.

Still, if you’re trying to create some kind of very highly optimized content, it could potentially be more efficient to use bespoke classes with very short names.

## 4\. Tailwind can’t do everything

While the capabilities of Tailwind are increasing all the time, there are some CSS properties and advanced techniques that are outside the scope of what it can do. This means that occasionally, you may have to add some inline styles or create some custom classes alongside Tailwind to get things done. Is this terrible? Not really, but it does mean that Tailwind isn’t a panacea for all needs.

## 5\. It could stop you from learning CSS properly

If you are *very* new to CSS, I wouldn’t recommend you use Tailwind because you should learn how CSS works first. You need to understand.

* most of the selectors (id, class, element, spaces, adjacent element, and so-on)
    
* [CSS precedence](https://css-tricks.com/precedence-css-order-css-matters/) – in what order does CSS apply?
    
* [Specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) – how the browser calculates which CSS applies (and which doesn’t)
    
* How common, frequently used CSS properties work
    
* How the [CSS box model](https://www.w3schools.com/Css/css_boxmodel.asp) works
    
* How flexbox works and how to use it
    
* The basics of how CSS grid works
    

All of this can take several years to master, so jumping straight into using a framework like Tailwind will leave you with some huge knowledge gaps that could affect your ability to do web design competently and compromise your ability to find work. Using Tailwind is convenient when you already understand CSS, but relying on it to compensate for a poor understanding of CSS is a bad idea.

## 6\. It reduces the separation of concerns between content and style

The original philosophy of CSS was that you should separate your style (CSS) from your document structure and content (HTML). If you can do this, a designer can easily change the style of a document without touching any of the HTML and impacting the content.

A canonical example of this is [CSS Zen Garden](http://www.csszengarden.com/), a website that has many radically different appearances by virtue of a set of 3rd-party stylesheets.

The creator of Tailwind, Adam Wathan, [wrote a document](https://adamwathan.me/css-utility-classes-and-separation-of-concerns/) explaining why separation of concerns is a straw-man argument that doesn’t hold up in the real world. The thing is, that in a real project of any complexity, either your CSS depends on your HTML or your HTML depends on your CSS, and they are very hard to separate.

Have you ever had a large project for which you completely refactored the HTML without changing any CSS? Or one in which you were going to restyle the site completely without adjusting any HTML? Not likely!

I think in practice, this is not a strong argument against Tailwind, but if you think this is important for the way you work, it is worth considering.

## Conclusion

If you were on the fence about trying Tailwind or were a detractor of it for some reason, I hope this article shines some light on why its fans love it so much. It offers so many advantages for speed of development, maintainability, and efficiency. Besides all that, it has a great ecosystem around it of UI components and existing designs you can borrow, [excellent documentation](https://tailwindcss.com/), and [tutorial videos available for free on YouTube](https://youtube.com/c/TailwindLabs).

If you enjoyed this article, please share it with your friend.