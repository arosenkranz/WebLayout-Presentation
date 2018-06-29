## Questions from Chat: 

Q: Does the sticky property acts like absolute, or does it "leave" a block behind somewhere?
> It does hold the space as if it was still there so following content doesn’t collapse into it.

---

Q: Is display: flex not supported as well? Or is it just the old display:flexbox?

> Display: flex is the only supported value, “flexbox” and “box” are not valid

--- 

Q: Have any of you toyed with Flexbox Froggy or Css
> Yes Flexbox Froggy & CSS Grid Garden are great (https://cssgridgarden.com/)

---

Q: How do flexbox and css grid play together?
> You can really use any combination of them you need, which is great.

>You can use Grid for overall section layouts and when you need to overlap content or span multiple rows (have more control) or… Use Flexbox for handling repeated content areas, like blog posts or portfolio items / galleries. 

> You can also use Flexbox really quick to achieve simple horizontal/vertical alignment in your items and layout little components.

> Ultimately, you can mix and match as you see fit. Just try and think of piece of your UI as a self contained component that you can design it on it’s own then place it into its parent container as you see fit

---

Q: Quick question about hand coding the css: this is great to get a feel for css, but don't most professional web devs use a framework like bootstrap and/or materialize? seems like using a framework speeds up development immensely. i sometimes combine vanilla css with a framework. i love materialize which does a lot of what you are demonstrating.

> There’s definitely still a place for frameworks as they do general layouts incredibly well (and the code is done for you), but it’s still important to know what’s making those frameworks tick under the hood.

> As time goes on, however, frameworks may feel limiting and / or bland and leave you wanting to create something more custom for your content. CSS Grid especially empowers you to create seemingly impossible layouts that were once reserved for print publications. I personally believe that we’ll start seeing a great shift in how application UI’s are constructed now that Grid is available to everyone.

---

Q: Have you run into any situations where Flexbox and CSS grid were not suitable for your situation?

> If I need to get up and running fast with a generic grid system I’ll probably still lean on Bootstrap or another prebuilt grid system, but overall you can really achieve anything you’re looking for with these two methods short of having fixed or sticky content.

--- 

Q: What disadvantages, if any, to using Flexbox?

> Flexbox only operates on one axis at a time (either column or row), so if you have to position something in a very particular way then Flexbox may not be the solution compared to Grid. 

---
Q: Is Grid responsive by default?

> That depends on how you define the column/row sizes. Like anything else, if you set these sizes in pixels (px) then it won’t be responsive since they’ll always fill in those spots. If you use percentages or even better, the “fr” unit, the grid will grow and shrink as you need. 

> To take this further, I suggest looking into defining your grid columns using the minmax(minValue, maxValue) to define “what is my smallest and what is my largest” values.

--- 

Q: What is your favorite way to implement these in React?

> So in React you have about 3-4 solid ways you can write your CSS and all of them are valid (global stylesheets, component styles that are imported, inline styles, or using a library like Styled Components/Glamorous)

> I think if you’re building a component library of reusable content, you can set up the Grid to have a global definition and be applicable anywhere in your content but then have those individual components have their own styles created inline (think form elements being built with Flexbox).

> The idea behind this is I can realistically build a bunch of components then reuse them across projects and they’ll maintain their structure/layout, allowing specifics (colors, font-family, functionality, etc) to be passed in as “props” that provide context to the component.
