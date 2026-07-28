# Parsimony Project

## About this Project

For some time, I've been thinking about certain high-level problems in the software world.  Mostly, I'm doing this just for the sheer mental exercise rather than to accomplish anything specific. (That's the philosopher in me, I guess.)  Please forgive the following ramble.

### Software Development is Solving Problems

People think that being a developer involves writing code, but I typically describe it as solving problems: solving technological problems directly, or using technology to solve non-technological problems.  When I think about the problems we need solved, I wonder about our increasing reliance on _external services_.  By 'services' I mean both code libraries and fully-fledged services, and by 'external' I mean any that are not directly created or controlled by you or your organization.  There are varied issues that arise with this type of reliance.

To start: Not all uses of external services are bad.

* Some external dependencies are actually quite sensible.  If your project involves machine learning or cryptography, you probably shouldn't try to write that yourself.
* Some project scopes inherently extend beyond our control.  If the project's functional requirements involve contacting some external API, then that dependency is unavoidable unless the requirements are wrong.

You could also unfavorably describe using a search engine or documentation as a form of external dependency. While that's true to a certain extent, it's less of a concern here because the dependency is not preserved within the project itself.  The knowledge and behavior will bake itself into the code and continue independently into the future.

If we exclude these acceptable exceptions, there are still plenty of small-to-medium sized problems that people need solved.  I feel like we sometimes tend to over-complicate them with additional dependencies.  Why?  How?

### Inherent Language Dependencies

When I want to solve a problem for my own curiosity, I typically use C#.  It's my primary competency and personal favorite programming language.  The issue is that C# code is not the easiest to share in a usable state.  Some typical hurdles include:

* The consumer needs the right .NET frameworks on their computer to manipulate your code (and probably an IDE).
* The compiled output cannot be reviewed by the end user.
* The code may or may not run on someone else's machine.

I'm not picking on C# here: the same is true for many other languages.  For a professional project, these are not a big deal because normal consumers will be prepared for these expectations.  They are a greater problem if your audience is someone in the general public and/or a non-developer.  What I'm seeking here is simplicity comparable to giving someone a .PDF or a .XLSX/.DOCX file.

### External Library Dependencies

External libraries are a good thing because it allows you to focus on conducting impactful work instead of trying to figure out a common problem.  But these are not without their issues:

* Some external libraries and/or services will end support, cease operation or the project might fork and split the community resources.
* Some cheap/free services may add or increase monetization in unexpected ways in the future.
* Some external libraries will have to introduce breaking changes that require your time and intervention.
* Some libraries and/or services could be found to have security vulnerabilities or be subject to a targeted attack to inject them, putting every consumer could be at risk.  (It's called [Dependency Chain Abuse](https://owasp.org/www-project-top-10-ci-cd-security-risks/CICD-SEC-03-Dependency-Chain-Abuse) and it would be no fun if it suddenly became your problem.)

Depending on your project, these will vary in their level of seriousness, but it would be nice to avoid many or most of these.

### Service Issues: Opacity, Availability, Privacy, Economy

If you want a problem solved, sometimes you can just find some website that already does it for you.  This is often fine enough, but this approach can raise questions questions:

* Is the code doing what you think it's doing?  Is there an arithmetic error?  Would you disagree with the problem-solving methodology?  Could you even understand it if you could read it?  
* Is the service available without the internet?  What if the services goes offline while you still have need of it, temporarily or forever?
* Is there a privacy or security concern in using this external service?  Even if your problem is harmless, what is the cost of that kind of trade off?
* Is this service using an amount of resources that are proportional to the value of the problem being solved?  Are you offloading a greater amount of work than it would take to do it yourself?  Is the imputed cost of your time and labor to create something greater than the total cost of your solution, even if you are not explicitly bearing the cost yourself?

### These Concerns as a Lens

Some or all of these could apply to a standalone website widget or, as is the style in 2026, a general purpose LLM chatbot that obsequiously purports to do the same things.  In this age of intellectual indolence, I think we are forgetting the value of a specialized tool.  Chefs have several types of knives made for different tasks, but LLM vendors want us to use their chainsaw for everything.

The point isn't to criticize any specific solution or choice.  Instead, I want to use this perspective as a lens to consider future work.  I think it is uncontroversial to say that for the most part we want to work efficiently, to do the correct work, and to not have our work wasted or lost.  

In software, we have the advantage of preserving our work and our understanding through time much more easily than most physical pursuits.  There are two main ways to do this are source control and unit testing.  What I'm talking about is something less impactful than those two, but still potentially worth exploring. 

## Parsimony in Software
I feel like the best answer is approach problems with _parsimony_.

* Use the least amount of effort to solve the actual problem.
* Front-load the effort where possible.
* Keep is simple and understandable.
* Make the solution as independent and atomic as possible.

There are other things we want, like transparency, clarity, portability and durability.  However, if we can keep things parsimonious, those will come more easily. 

### Framework for Parsimony
If we're trying to avoid the dependencies and issues above, what type of framework can we use to make sure anyone can use it?  What do we have access to that we know will work almost anywhere?

My thought was to work entirely within HTML, vanilla JavaScript and maybe a little CSS.  Using these technologies, I see the following advantages and disadvantages:

### Advantages
* Any dependencies will already be present on any modern operating system and it should run in basically all modern web browsers.  (It would not even require the actual internet: just the browser.)
* Something written this way can all be packed into a single file. (Modern sites import their .js and .css files, but they can just be hard-coded into the \<script\> and \<style\> elements.)
* The code will be unconcealed, and can be intentionally made readable to create a low barrier to understanding it.  (A person could probably ignore the HTML and CSS, treating it as 'boilerplate' and focus on understanding the bulk of the behavior within the JavaScript.)
* No undue concerns over security, privacy, or energy use.  (The scope is kept narrow and there are no references to any outside party.)

### Disadvantages
* There will be some reasonable limitations on what we can do with this tech stack.
* It will take longer to create these tools than to use an existing one someone else has created.
* This strategy could favor using many hard-coded values as well as 'more-readable yet less-efficient' code, which might violate some principles of good engineering.
* Spreading editable code to multiple team members would allow for behavioral discrepancies if people make individual changes.
* I just don't really like JavaScript very much. :wink:

I think the benefits outweigh the downsides.

My goal here is not to say all problems should be solved this way.  Instead, I am wondering how many problems _could_ be solved within this mental framework.  Rather than offloading my thinking to an existing machine, how can I work smarter instead of making someone else do the hard work?

## How to Use

Using these tools should be simple.  They are kept in the repo's Tools folder.  From there, all that is needed is to download the HTML file and open it in the browser of your choice.  GitHub does not appear to offer the ability to open an HTML file in your browser by default.  (In some ways, that would be missing the point.)

The tools themselves should be fairly self-explanatory, considering the relatively straightforward scope of problems they are likely to tackle.  At the moment, I am not prescribing any top-level style or concerns except that each is entirely contained in one singular HTML file.

## Technology Used

I used NotepadQQ and Librewolf to make this.  I have not tested on other browsers, but they should probably work fine.  To brush up on frontend tech, I mostly used w3schools.com and posts on stackoverflow.com found via DuckDuckGo.  I also sometimes use JetBrains Rider for a few niceties of a proper IDE and git diffs.

No generative AI was used when creating this.  (Since people have decided to cram generative AI into everything, it's hard to say for _certain_ there is none present here, but I'm as confident as I can be.)  The point of this project was never really to simply 'make the thing' though that's a nice side benefit.  The point was to take the opportunity to think about the making.

## Questions
There are some stylistic questions about how to approach this type of coding:

* For repeated HTML elements, is it better to copy-paste code and violate DRY (Don't Repeat Yourself) or do we use vanilla JavaScript to build the HTML elements systematically, which will increase the opacity of the code?
* Is it okay to hard-code some elements to embrace YAGNI (You Ain't Gonna Need It)?  Or should we focus on designing more reusable code snippets, even if they're being copied about manually?
* What about things like arrow functions (what we would call Lambda expressions in C#)?  Do those inhibit clarity to a more casual observer?  Is it fine to write longer, less efficient but simpler code?

There are other non-code questions to ask as well: 
* Are we overestimating how many problems are simple enough that they can actually be handled in this way?  It feels like the 'input data' must be comparatively lean and simple for this to all exist in one spot.  Something containing historical data like sports scores or stock prices might be unwieldy to use in this form, but that may not matter if it's treated as 'magic dust' as my professor used to say.  It isn't as if the size of the file will be relevant to a consumer unless they dive into it.

Other questions may arise as I play in this framework and review other problems.

## License Information
This project is © John Hibbert and licensed under the terms of the MIT License.
