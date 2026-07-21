# Parsimony Project

### About this Project

For some time, I've been thinking about certain high-level problems in the software world.  Mostly, I'm doing the thinking for the sheer exercise of it. (That's the philosopher in me, I guess.)  The main thing I think about is our increasing reliance on external services.  By 'services' I mean both code libraries and actual fully fledged services, and by 'external' I mean ones that are not controlled by you or your organization.

To start: Not all uses of external services are bad.  

* Some external dependencies are actually quite sensible.  If your project involves machine learning or cryptography, you probably shouldn't try to write that yourself.
* Some project scopes inherently extend beyond our control.  If the project's functional requirements involve contacting some external API, then that dependency is unavoidable unless the requirements are wrong.

Now, you could also unfavorably describe using a search engine or documentation as a form of external dependency. While that's true to a certain extent, it's less of a concern here because the dependency is not preserved within the project itself.  The knowledge and behavior will bake itself into the code and continue independently into the future.

If we exclude these acceptable exceptions, there are still plenty of small-to-medium sized problems that people need solved.  I feel like we sometimes tend to over-complicate them with these dependencies.  Why?

#### Inherent Language Dependencies

When I want to solve a problem for my own curiosity, I typically use C#.  It's my primary and favorite programming language.  The issue is that C# code is not the easiest to share.

* A consumer needs the right .NET frameworks on their computer to manipulate your code.
* The compiled output cannot be reviewed by the end user.
* The code may or may not run on someone else's machine.

I'm not picking on C# here: the same is true for many other languages.  For a professional project, these are not too big of a deal because the consumers will have these expectations already.  They are a greater problem if your audience is someone in the general public and/or a non-developer.  I seek simplicity comparable to giving someone a .PDF or a .XLSX/.DOCX file.

#### External Library Dependencies

External libraries are a good thing because it allows you to focus on conducting impactful work instead of trying to figure out a common problem.  But these are not without their issues:

* Some external libraries and/or services will end support, cease operation or the project might fork and split the community resources.
* Some cheap/free services may add or increase monetization in unexpected ways in the future.
* Some external libraries will have to introduce breaking changes that require your time and intervention.
* Some libraries and/or services could be found to have security vulnerabilities or be subject to a targeted attack to inject them, putting every consumer could be at risk.  (It's called [Dependency Chain Abuse](https://owasp.org/www-project-top-10-ci-cd-security-risks/CICD-SEC-03-Dependency-Chain-Abuse) and it would be no fun if it suddenly became your problem.)

Depending on your project, these will vary in their level of seriousness, but it would be nice to avoid many or most of these.

#### Service Opacity, Privacy and Energy

Sometimes if you want a problem solved, you find some website that already does it for you.  But this approach is not free of questions:

* Is the code doing what you think it's doing?  Is there an arithmetic error?  If you could see it, could you even understand it?  Would you disagree with the methodology?
* Is there a privacy or security concern in using this external service?  Even if your problem is benign, what is the cost of that kind of trade off?
* Is this service using an amount of resources that are proportional to the value of the solved problem?  Are you offloading a greater amount of work than it would take to do it yourself?  (This is especially true recently.)

Each of these could apply for a standalone website widget or, as is the style in 2026, a general purpose LLM chatbot that obsequiously purports to do the same thing.  In this age of intellectual indolence, I think we are forgetting the value of a specialized tool.  Chefs have several types of knives made for different tasks, but LLM vendors want us to use their chainsaw for everything.

Taken together, these issues with the software world may or may not apply to a any given problem, but many of them apply to many problems.  I want to use this perspective as a lens to consider future work.

### Parsimony in Software
I feel like the best answer is approach problems with _parsimony_.   Use the least amount of effort to solve the actual problem.  Front-load the effort where possible.  Keep is simple and understandable.

If we're trying to avoid the dependencies and issues above, what type of framework can we use to make sure anyone can use it?  What do we know that will work almost anywhere?

My thought was to work entirely within HTML, vanilla JavaScript and maybe a little CSS.  We won't be importing any outside JavaScript libraries.

Using these technologies, I see the following advantages and disadvantages:

#### Advantages
* Any dependencies will already be present on any modern operating system and it should run in basically all modern web browsers.  (It would not even require the actual internet, just the browser.)
* Something written this way can all be packed into a single file. (Modern sites import their .js and .css files but they can just be hard-coded into the \<script\> and \<style\> elements.)
* The code will be unconcealed, and can be intentionally made readable to create a low barrier to understanding it.  (A person could probably ignore the HTML and CSS, treating it as 'magical fairy dust,' and focus on understanding the bulk of the behavior within the JavaScript.)
* No undue concerns over security, privacy, or energy use because the scope is narrow and there is no reference to any outside party.

#### Disadvantages
* There will be some reasonable limitations on what we can do with this tech stack.
* It will take longer to create these tools than to use an existing one someone else has created.
* This strategy could favor using many hard-coded values as well as 'more-readable yet less-efficient' code, which might violate some principles of good engineering.
* I just don't really like JavaScript very much. :wink:

I think the benefits outweigh the downsides.

My goal here is not to say all problems should be solved this way.  Instead, I am wondering how many problems _could_ be solved within this mental framework.  Rather than offloading my thinking to an existing machine, how can I work smarter instead of making someone else do the hard work?

### Tools Used

I used NotepadQQ and Librewolf to make this.  I have not tested on other browsers, but they should probably work fine.  To brush up on this frontend tech, I mostly used w3schools.com and posts on stackoverflow.com found via DuckDuckGo.

No generative AI was used when creating this.  (Since people have decided to cram generative AI into everything, it's hard to say for _certain_ there is none present here, but I'm as confident as I can be.)  The point of this project was never really to simply 'make the thing' though that's a nice side benefit.  The point was to take the opportunity to think about the making.

### Questions
There are some stylistic questions about how to approach this type of coding:

* For repeated HTML elements, is it better to copy-paste code and violate DRY (Don't Repeat Yourself) or do we use vanilla JavaScript to build the HTML elements systematically, which will increase the opacity of the code?
* Is it okay to hard-code some elements to embrace YAGNI (You Ain't Gonna Need It)?  Or should we focus on designing more reusable code snippets, even if they're being copied about manually?

Others may arise as I play in this framework and review problems.

### License Information
This project is © John Hibbert and licensed under the terms of the MIT License.
