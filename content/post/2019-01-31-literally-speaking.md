Date: 02/02/19
Title: Literally Speaking
Permalink: /literally-speaking
Tags: learning, coding

# Literally speaking

Yesterday I [put in a pull request][pr] for the framework that we use at work. It was related to [an issue I'd submitted][issue]; namely, that I wanted to be able to send folks style guide links to specific variants of components we build. 
{{more}}
Building this had a lot of codey type things in it:

- Thinking about how to build it took longer than building it! This happens not infrequently, but it's definitely surprising to newer folks.  
- I played a bit with regular expressions. Regex is a weird thing, but I didn't want to have spaces in URLs, since those can still cause problems. A bit of googling found me the expression I needed, but I also had to fully understand the JavaScript in order to do it. 
- JavaScript! I'm working on learning a lot more JS; I _think_ it's a case of "I know more than I think I do," but also, it took me a minute to figure out how to do this:
 
```
            // for permalinks to examples
            const exampleName = example.name;
            const exampleNameNoSpace = exampleName.replace(/\s+/g, '');
            const exampleLink = `#${exampleNameNoSpace}`;
```
However, I did it!

You see, when you look up examples for using these sorts of expressions, programmers like to use variables (like `str` for string) that feel like they mean more than they do. So many examples used `str.replace(/\s+/g` that I thought it meant something important.  Nope! This was just convention, used by many folks, but not necessary. 

And hey, it worked!

***

One of the main things I had to figure out is how .jsx -- combined with the linting we use -- would want me to combine the `#` needed for [an anchor link on the same page][anchor] with the `exampleNameNoSpace` variable I'd created above it.  

These are "[template literals][literals]," and though I could have concatenated the two parts, [ESLint wasn't having it][lint]. The cool thing is that _the linter's warning taught me a new thing I needed to know_. 

So yeah! That's what I learned yesterday. How bout you?
- 

[anchor]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a#attr-href
[pr]: https://github.com/drolsen/Unslated/pull/106
[issue]: https://github.com/drolsen/Unslated/issues/99
[lint]: https://eslint.org/docs/rules/no-useless-concat
[literals]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals