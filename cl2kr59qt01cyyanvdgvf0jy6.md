## Modern Frontend: Growing Responsibilities

> **TLDR:** The increasing complexity in the frontend ecosystem should trigger a reassessment of valuation, job descriptions, and general overview of frontend developers.

## Intro 

Lewis Caroll's description of  Wonderland, as a place where “It takes all the running you can do, to keep in the same place. If you want to get somewhere else, you must run at least twice as fast as that!”, which epitomizes the current landscape of frontend engineering where standards evolve and change is the only constant.

Several months ago, I stumbled upon an intelligently written [piece](https://bradfrost.com/blog/post/front-of-the-front-end-and-back-of-the-front-end-web-development/) by [Brad Frost](https://bradfrost.com/) on what had then begun to be called [The Great Divide](https://css-tricks.com/the-great-divide/). This made the rounds. In this article, he outlined two functionally distinct aspects of web development: **Front-of-the-front-end web development** and **Back-of-the-front-end web development**.

> NB: In this post, I do not give heed to the nuances of syntax. As such "Front-End", "Frontend", "Front end" would refer to the same aspects of web development neither do I concern myself with the semantic differences, if there are any, between "Developer" and "Engineer". All terms would be used interchangeably in this write-up.

It’s become more prominent in recent times that the term "Front-End Developer/Engineer" needs an overhaul, with reasons stemming from the ever-expanding surface area of responsibilities that have to be catered for and categorized as "Front-End".

In line with this, various points were raised stating that the minefield that is CSS is a big enough challenge. As bluntly put by [Mandy Michael]() in her article, [Is there any value in people who cannot write JavaScript?”](https://medium.com/@mandy.michael/is-there-any-value-in-people-who-cannot-write-javascript-d0a66b16de06)

>When every new website on the internet has perfect, semantic, accessible HTML and exceptionally executed, accessible CSS that works on every device and browser, then you can tell me that these languages are not valuable on their own. Until then we need to stop devaluing CSS and HTML.

Here she puts forth the brilliant idea, that although a divide exists, it doesn't exist for the casting down of one side or the other.

Addressing the differences between developers [Ronald Long](), in the context of peace, wrote in his [article](https://webdesigntips.blog/web-design/css-tricks/the-great-divide/) on the subject:

>Yes, there is a divide, but no, neither side is any more valuable than the other.

It is worthy of note that the divide being spoken of here refers to how the broader ecosystem splits the responsibilities of the frontend developer into two sections. Those who major in HTML and CSS (front-of-the-frontend developers) sometimes referred to as UI developers and those that are far more dependent on Javascript (back-of-the-frontend developers).

However, most times this distinction only serves to educate the developers themselves as employers and recruiters do not give heed to the growing landscape of responsibilities of the frontend developer. As such most frontend developers are expected to be both front-of-the-frontend and back-of-the-frontend savvy.

This results in a , as requirements for frontend developers now differ significantly from those of a few years ago. The developer community, in an attempt to capture the current state of frontend engineering, has adopted the term **Modern Frontend**.

Sadly, this doesn't appear to have gained traction with many people. The common sentiment (in my experience) by other engineers and those in management, towards what is regarded as frontend, hasn't shifted to reflect the expansion. Particularly in the context of regard and valuation.


## Possible Reasons 

Based on personal experience as well as those of the numerous articles I've read on the topic, I can classify the justification for the resilience to change in perception into two classes:
Sentiment
Responsibility
These are highlighted in the reasons that follow.

Recently, I came across a brilliant article on [Frontend Vs. Backend System Design Interviews](https://www.zhenghao.io/posts/system-design-interviews), where the author gave his two cents (more than that though) on the context, similarities, and differences in interview processes between jobs listed for Frontend and Backend Developers/Engineers.

The author, [Zhenghao](https://twitter.com/he_zhenghao), also expressed a concern for a [Career Ceiling](https://www.zhenghao.io/posts/system-design-interviews#career-ceiling) which seems to be exclusive to frontend engineers only. This is in line with intermittent opinions that pop up every now and then saying or implying that *"frontend engineering isn't real engineering"*.

The author along with anyone that has paid attention to the frontend ecosystem knows that frontend is just as much as challenging as backend.

However, it's quite important to recognize the underpinnings of such statements. Paraphrasing some of the opinions from [Zhenghao](https://twitter.com/he_zhenghao) in [this post](https://www.zhenghao.io/posts/system-design-interviews), possible reasons include:

### Inertia

The reluctance to a change in the mentality that frontend is not real engineering can be seen quite clearly in differences in compensation.

At the time of writing, estimations from [Glassdoor](https://glassdoor.com/) inform of a pay gap of 10 - 70% between Frontend and Backend developers for roles with similar experience depending on the industry and location.

Also, this can be seen in the roles of those that move up the career ladder. Depicted in how most (from those I’ve seen) of VP of Engineering or CTOs were previously Backend Engineers or Infrastructure(DevOps) Engineers. I give more details on my reasoning around this in the section on [experience](#heading-experience).

### Economics

This reasoning values an engineer by the amount of money(resources) you control. This can also be referred to as responsibility.

As noted by [Zhenghao](https://twitter.com/he_zhenghao) in his article,

>I had this realization that when I was going through the backend system design interviews vs. the frontend system design interviews - the technical topics those interviews tend to cover let me think about some economic reasoning leading to the perception of a "Frontend Ceiling” as well. 

Backend systems require more expensive resources to run, be it Digital Ocean droplets, EC2 instances etc. These compute seem to require much more to both maintain and scale.

Frontend systems on the other hand run on the user's devices, which costs a company essentially...NOTHING! No maintenance is needed. No bills.

Essentially, bad backend code or DevOps integrations can lead to a hefty bill from AWS that'd make anyone cry, but bad frontend code can be seen to mostly affect a user to a certain degree and doesn't drain the funds of the company.

### Length of processes

Frontend applications live on the user's device, spun up, and terminated with the open and close of a browser tab. While backend application servers however run for months and or years.

Flawed frontend code only lives long enough to affect the currently open tab. Flawed backend code however can and often will accumulate, leading to slowdowns or crashes. One can be ignored the other most certainly cannot.


### Experience

This point is from my personal experiences in the tech space. It's easy to associate the term frontend with inexperience. In reality, it is relatively newer due to the technologies that surround it.

From my research, when web browsers were first released there wasn’t much of a “front-end.” There were static HTML pages and CGI scripts that generated HTML.

Asynchronous JavaScript and XML (Ajax), from its inception in 2004 (or 1999 depending on who you ask) then until its proliferation in 2008/2009 periods wasn't widely adopted.

JavaScript, which serves as the base for modern frontend, wasn't as used till frameworks that emerged around the 2010s. Developers around these periods worked largely on the backend (server-based tasks, databases, etc). Backend developers that then worked on user interfaces are styled, Fullstack Developers.

This largely leaves **mostly** newer developers who focus on the front-facing interface to embrace the “frontend” description. Thereby easy to associate them with fewer years of experience.

Coupled with the fact that frontend (referring to HTML, CSS, and JS) has the least barrier to entry–a web browser. As such beginner web developers are advised to start with HTML, CSS, and JS which are the fundamentals of frontend.

These are brilliant points!👏🏾

However, I hold other opinions which do not invalidate the points listed above, but rather take into account how broad the Front End ecosystem has become.

This is due, largely, to user expectations which have led frontend down a road of solutions that succumb to incidental complexity.

>Frontend isn't working hard to become as complex if not more than backend.

The need to adapt to the end-user, to maintain a stable pace with advancements in browser technology, devices, web standards, etc has led to newer(sometimes weirder) solutions in the frontend ecosystem.

>The definition of the frontend role has expanded to include human-computer interaction, responsiveness, UI optimization and reusability, browsers, devices, and accessibility amongst others.

Over the last couple of years, there has been an explosion of options for nearly everything in the ecosystem some of which I highlight in the next section.


## Rising Frontend Complexity

With almost every passing week emerges new abbreviations and concepts, further expanding the body of knowledge. 

Sophisticated abstractions intended to ease the workload on engineers tend to demand new understanding and inspire new ways of building apps. Complexity in itself doesn't attenuate, it only evolves.

> Change is rapid and unpredictable.

The increase in internet usage shows that web developers now have to consider a larger audience, tougher demands, and offer better user experience by whatever means necessary.

All in a space that's come under more scrutiny in recent times with Google's announcement to rank pages based on Core Web Vitals. Frontend developers as such have to resort to more nuanced technologies to meet egregious and ever-rising demands while balancing what tradeoffs may come their way.

Modern frontend has spurred the demand for pixel-perfect, real-time, reactive, concurrently rendered, responsive sites with minimal bundle size, accessible HTML & CSS, stylish UI with snappy responses, optimistic updates, cached data, and performant animations across all devices to which newer features can be easily added without a hit to performance or developer productivity.😰

Really, is that all? Want my left hand too?🙄

There also exist different ways to achieve similar results, all with their nuances and learning curves. This has led to the further rise in complexity of frontend architecture. Some categories of these choices include:

### 1. Tooling 

**Frameworks:** React, Vue, Angular, Solid, Svelte, Qwik
**Frameworks:** NextJS, Remix, NuxtJS, Sveltekit
**Bundlers:** Vite, Snowpack, Webpack, Parcel, Rome
**State managers:** Redux, Zustand, Recoil, Pinia, Vuex
**Package managers:** npm, Yarn (1,2,3), pnpm
**Serverless:** Netlify functions, Vercel edge functions, Cloudflare workers, AWS Lambda
**Project structure:** 😂 

Frontend tools are no longer presented as optional features. Developers can only handle so much complexity on their own before relying on useful abstractions to solve routine tasks.

Libraries and tools were born out of necessity, the need to adapt to tougher requirements as well as the desire for the better developer experience. The model of modern frontend therefore favours configuration and flexibility.

The plethora of choices when it comes to tooling is both a blessing and a curse. For example, if some better architectural model surfaces tomorrow there’s a good chance it’d be available sooner rather than later. Here, it’s a blessing.

However, this means frontend developers have to weigh `x+1` factors in making the choice of tools to use. [Vadim Demedes](https://vadimdemedes.com/) laments about this in [his article](https://reviewbunny.app/blog/dont-make-me-think-or-why-i-switched-to-rails-from-javascript-spas) where he explains why he switch to rails from javascript single page applications.

### 2. Various rendering and hydrations modes

It really does seem like everyone is trying to come up with three letter acronyms for new rendering modes.

CSR - Client Side Rendering
ISR - Incremental Static Regeneration 
DPR - Distributed Persisted Rendering
DSG - Deferred Static Generation 
SSR - Server Side Rendering 
SSG - Static Site Generation
There’s more coming!

These would be explained in a different blog post. Watch out! 

Also, for the types of applications there’s the choice between:
SPA - Single Page Applications
MPA - Multiple Page Applications
Hybrid
The best resource I have come across on the topic can be found [here](https://kissdigital.com/blog/single-page-application-how-spa-works-and-how-it-differs-from-mpa)

Not to mention the different modes of hydration i.e Progressive hydration, selective hydration, or sidestepping hydration altogether and going for a framework that favours [resumability](https://www.builder.io/blog/from-static-to-interactive-why-resumability-is-the-best-alternative-to-hydration) (thank you [Misiko](https://twitter.com/mhevery)!).

This might seem to be a challenge mostly faced by authors and maintainers of libraries, who work immensely to create sane abstractions for the developer community. 

For example, to switch from SSR to ISR in NextJS can be the addition of a single line of code.

However, note that frontend developers being burdened about user experience and performance have to weigh the tradeoffs between the different modes and the community that surrounds them. 

At the point of writing, it is quite possible to ship relatively complex web apps built without an explicit backend. Thanks to hybrid frameworks frontend has gone fullstack!


### 3. Evolution of the web and user expectations

The web is poised to become its own operating system, allowing developers to bypass building the same app for different platforms.

With the rising CPU performance of devices, phones and computers can do more and users have come to expect more. This can be seen in Line Engineering’s [report](https://engineering.linecorp.com/en/blog/the-baseline-for-web-development-in-2022/) on web development.

Versions of popular apps such as VScode, Photoshop etc are now available on the web.

The usefulness of a site ultimately comes down to user interactions. This can yield beautiful rewards for the business as a whole when done right as well as reap alarming consequences when gotten wrong. 

In 2015, [Invision](https://www.invisionapp.com/) published an [article](https://www.invisionapp.com/inside-design/statistics-on-user-experience/) with compilation of statistics on the effect of UX on businesses. Simply put, the [ROI of UX](https://www.toptal.com/designers/ux/roi-of-ux-convince-executives) cannot be overlooked.

## Conclusion

I wrote this piece, not as a swipe at other forms of engineering, because they do have various choices to make and also have to handle rising complexity. The point of this article was to show that frontend ought to be appreciated alongside the immense work being done by engineers all around.

Truly, this is a hard and exciting time to be a frontend developer. As Kevin Ball put it, in his [article](https://blog.logrocket.com/the-increasing-nature-of-frontend-complexity-b73c784c09ae/)

>The technology is moving so fast it’s hard to keep up, the ecosystem is fragmented, and there is tremendous pressure for even individuals to meet and exceed the user experience standards set by massive billion-dollar companies.

Work requirements are evolving in all spheres, likewise, it's important to update our assessments of all roles.

This is an incredible time for innovation, there have never been more opportunities, and there has never been more powerful tooling.

This is an amazing time to be a Front End developer ✌🏾


## Resources

1. https://www.youtube.com/watch?v=grSxHfGoaeg
2. https://webdesigntips.blog/web-design/css-tricks/the-great-divide/
3. https://blog.logrocket.com/the-increasing-nature-of-frontend-complexity-b73c784c09ae/
4. https://www.zhenghao.io/posts/system-design-interviews
5. https://css-tricks.com/the-great-divide/
6. https://bradfrost.com/blog/post/front-of-the-front-end-and-back-of-the-front-end-web-development/
7. https://engineering.linecorp.com/en/blog/the-baseline-for-web-development-in-2022/
8. https://reviewbunny.app/blog/dont-make-me-think-or-why-i-switched-to-rails-from-javascript-spas
