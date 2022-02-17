## A Guide to Order: Setting up Prettier and Eslint with Husky, Lint-staged and Commitizen

>**TLDR:** To save yourself a headache, use [coding standards](#heading-the-what-why-and-how-of-coding-standards) and become more efficient by [automating your development workflow](#heading-set-up-husky-and-lint-staged).


## Intro

Have you ever had to code review a PR that has 2000+ changes, when the actual code change was less than 15 lines? I have and it’s quite annoying.

When we write code it is to the end that it’s understood by other developers and also your future self. As such we find value in guiding principles and conventions by which we’re able to develop in a consistent manner. This is the very reason for coding standards.

>Order over chaos.

Coding standards are best-practices guides that developers follow in order to write code in a predictable and consistent manner. Basically, this makes it easier for the team to maintain and extend an existing codebase.

Engineers at their core tend to prefer automation over manual processes. Being willing to spend hours automating a task that’d take just a few minutes of manual labour. In like manner, there’s the obvious benefit of automating the enforcement of coding standards in a project.

**Yes, it’ll fix your errors without additional effort!!! 🎉**

This write-up contains explanations as well as a tutorial on how this can be done using Husky, Lint-staged, Eslint, Prettier, and Commitizen.


## Learning outcome

- Understand what coding standards are
- Understand the advantages of coding standards
- Understand git hooks
- Setup git hooks with husky and lint-staged
- Configure Eslint, Prettier, and Commitizen


## Prerequisites

- Node >= v14


>**NB:** As usual, I lean towards a thorough approach to learning and understanding, therefore I go through the explanations first outlining the benefits and answering why we need to set standards for every project in an organization.

Alternatively, if you’d rather just know how to set up the tools don’t worry I’ve got you covered. You can go directly to the tutorial section [here](#)


## The what, why, and how of coding standards?

Coding standards are a set of guidelines that recommend programming styles, practices, and methods for a given program.

**Why do we need them?** Because everyone writes code differently which is usually fine until you have to work with someone else's code.

In development, I generally go by the maxim:

> Prefer structure and consistency over style and comfort.

This presents benefits for every developer that’s working on and will work on the project.


### Benefits of coding standards

- It gives a uniform appearance to the codes written by different engineers.
- It improves the readability and maintainability of the codebase and it reduces complexity also.
- It allows catching of errors in their infancy
- It helps in code reuse and helps to detect errors easily.
- It promotes sound programming practices and increases the efficiency of programmers.

This is general aids developer productivity and speeds up work. It reduces the guessing game and revisions that newer developers have to go through when making contributions.


### Style guide

A style guide contains general rules about “how to write” code. This usually contains fine-grained instructions on how code should appear. These would provide guidelines for how the code should look, clearly stating [anti-patterns](https://en.wikipedia.org/wiki/Anti-pattern).

To quote [an article](https://medium.com/docon/airbnb-javascript-style-guide-key-takeaways-ffd0370c053) on the topic,

>“All code in any code-base should look like a single person typed it, no matter how many people contributed.”

Typical factors considered when choosing a style guide include:
Indentation: tabs or spaces, indent width
- Bracket placement
- Quotes to use
- Spacing
- Ordering
- Comment style and the use of documentary comments
- Variable, class, and file naming conventions
- Statement style and best practices of their usage
- File organization
- Declaration of classes and interfaces
- Exception handling
- Import and export types

For example, [Airbnb’s style guide for React](https://airbnb.io/javascript/react/) gives a perfect picture of the expectations of a style guide.

![Airbnb style guide 1](https://cdn.hashnode.com/res/hashnode/image/upload/v1645108848803/9cVp1Ryxv.png)

![Airbnb style guide 2](https://cdn.hashnode.com/res/hashnode/image/upload/v1645108862276/8_ZJEHwGoP.png)

More examples of coding standards can be found [here](https://github.com/housecricket/Coding-Conventions)

In practice, it’s important that all these have to be chosen by the team to ensure the standards fit the needs of the project and the developers involved. Coding standards for each team are different as such they have to be decided appropriately. In the end, it’s these developers as well as those that would come who will maintain the codebase. Therefore, they have to be considered when deciding on coding standards.

>**Suggestion:** Call a meeting with the dev team where coding standards are explicitly discussed and agreed upon.

Then, the golden question that this article aims to answer is, **how can I enforce this in my codebase?** 🤔


### Linting

[Linting](https://en.wikipedia.org/wiki/Lint_%28software%29) is the process of using a tool to analyzes source code to flag programming errors, bugs, stylistic errors, and suspicious constructs. This is done using a **Linter** or **Lint tool**.

The most popular amongst the lint tools is [Eslint](https://eslint.org/). According to the docs, 

>ESLint is a tool for identifying and reporting on patterns found in ECMAScript/JavaScript code, with the goal of making code more consistent and avoiding bugs.

Can be installed using:

```bash
npm install eslint --save-dev

# or

yarn add eslint --dev
```

To set up a config file:

```bash
npm init @eslint/config

# or

yarn create @eslint/config
```

This will create an `.eslintrc.{js,yml,json}` file in your directory. In it you’d find something like:

```json
{
    "rules": {
        "semi": ["error", "always"],
        "quotes": ["error", "double"]
    }
}
```

These rules guide Eslint when it scans your codebase to know what conventions you’ve specified to follow. 

Your `.eslintrc.{js,yml,json}` configuration file will also include the line:

```json
{
    "extends": "eslint:recommended"
}
```

This provides some (default standards](https://eslint.org/docs/rules) (all of the rules marked "✓") from Eslint. These can also be extended using Eslint’s rich plugin system. 

You can create and publish your own config, and can also install plugins from other creators from NPM. Some notable ones include:

- [Airbnb’s eslint config](https://www.npmjs.com/package/eslint-config-airbnb)
- [Google’s eslint config](https://github.com/google/eslint-config-google)

An alternative linter is [JShint](https://jshint.com/).


### Formatting

Prettier is an opinionated code formatter with support for various languages. It ensures that all outputted code conforms to a consistent style. Prettier takes your code and reprints it from scratch by taking your configuration into account. You can learn more [here](https://www.youtube.com/watch?v=hkfBvpEfWdA).

The docs present extensively the [benefits](https://prettier.io/docs/en/why-prettier.html) of using Prettier as a code formatter. Some of which include:

- Building and enforcing a style guide
- Helping Newcomers
- Easy to adopt

Can be installed using:

```bash
npm install prettier --save-dev

# or

yarn add prettier --dev
```


### Differences between linters and formatters

Linters analyze your codebase to catch errors and suggest best practices ( involving the use of the abstract syntax tree) while formatters fix code style. Linters should deal with tasks like function complexity, syntax improvements, etc while formatter should deal with tasks like spacing, line wraps, comments, etc.

**Linters can be used as formatters, but they are not the best fit for those classes of tasks.**

The Prettier documentation makes reference to (formatters vs linters](https://prettier.io/docs/en/comparison.html#how-does-it-compare-to-eslinttslintstylelint-etc), stating to:

>Use Prettier for formatting and linters for catching bugs!

Both do their job well as such should be used together.

However, there’s a known problem when using both Eslint and Prettier. A good approach is to run prettier first and then Eslint. There, however, exists a simpler solution. Enter [prettier-standard](https://github.com/sheerun/prettier-standard).

[Prettier-standard](https://github.com/sheerun/prettier-standard) helps to format with prettier (actually [prettierx](https://github.com/brodybits/prettierx)) and lints with [eslint](https://eslint.org/) preconfigured with [standard](https://github.com/standard/standard) rules. No eslint config has to be set.

**Tip:** On VScode, an extension that can make this experience better is [Error lens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens). This highlights sections of the codebase that require linting or formatting thereby creating a better experience for the developer.

![error lens](https://cdn.hashnode.com/res/hashnode/image/upload/v1645108953706/pm-zao9m-.png)


### Git hooks

Git hooks are scripts that Git executes before or after events such as commit, push, and pull. They can be used to alter internal behavior and receive notifications when certain events occur in a repository. Git hooks are built into Git so there’s no need to download anything. These Git hooks run locally.

Some example hook scripts include:

- pre-commit: Can be used to check that the commit message conforms to convention.
- post-commit: Can be used to email team members of a new commit.
- post-merge: Can be used to install new dependencies

A comprehensive list of Git hooks can be found [here](https://githooks.com/)

![Hook execution timeline](https://cdn.hashnode.com/res/hashnode/image/upload/v1645108991401/F8QPr0czU.png)


Hooks are regular scripts that reside in the .git/hooks directory of your project. This makes them easy to install and customize. They plug into the entire development life cycle. We now know how to perform customizable actions at every stage in the commit creation process, therefore can greatly increase developer productivity.

A more elaborate explanation of the hooks overview, concept, and scope can be found [here](https://www.atlassian.com/git/tutorials/git-hooks)



## Set up Husky and Lint-staged

### Install husky

First, we have to initialize husky. We do this using `npx`,

```bash
npx husky-init && npm i

#Or

npx husky-init && yarn
```

This would edit the package.json file by adding the husky dev dependency and the script,

```bash
"scripts":{
…
"prepare": "husky install"
}
```

This helps to install husky on other devices.

It also creates a `.husky` folder in the root directory.

```
|-- .husky/
   |-- _/
       |-- husky.sh
   |-- .gitignore
   |-- pre-commit

```

The pre-commit file contains a default script:

```bash
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

npm test
```

This script contains commands that’d run just before a commit is made. Let’s edit this to run type checks and test scripts before a commit is made.

>Omit the typescript portions of the script if you’re using Javascript

```bash
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

npm run tsc
npm test
```
And we add the script to the package.json

```json
"scripts":{
…
"tsc": "tsc",
"prepare": "husky install"
}
```

But there’s a problem. This would run the test files and type checks every time we change anything at all. To solve this we use lint-staged.
 ### Install Lint-staged along with Prettier and Eslint

Install lint-staged, prettier and eslint using,

```bash
npm i --save-dev lint-staged prettier eslint 
```

Lint-staged allows us to run scripts **only when** certain files are about to be committed. Let’s edit our package.json to reflect this,

```json
"scripts":{
…
“lint”: “eslint . --fix”,
"tsc": "tsc",
"prepare": "husky install"
}
…
"husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
"lint-staged": {
    "**/*.{js,jsx,ts,tsx}": [
 "npm run lint",
“npm run test --watchAll=false --findRelatedTests --bail”,
],
    "**/*.{json,css,md}": "prettier --write"
  },
```

>Please play around with the flags to obtain the suited result.

We can then go back to edit the pre-commit file,

```bash
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

npm run tsc
npx lint-staged
```

You can then add `.eslint.rc`, `.eslintignore`, `.prettier.rc` and `.prettierignore` as you see fit.

Now, when a commit is to be made lint-sage would run the type checker, eslint and prettier.

### Set up a commit message hook and Commitizen

The [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification is a lightweight convention on top of commit messages. It provides an easy set of rules for creating an explicit commit history.

We can create a hook that’d check if the commit message is according to the conventional commit standard.

To add a hook to check the commit message, run the command:

```bash
npx husky add .husky/commit-msg
```

Then paste in the script below,

```bash
#!/bin/sh
if ! head -1 "$1" | grep -qE "^(feat|fix|chore|docs|test|style|refactor|perf|build|ci|revert)(\(.+?\))?: .{1,}$"; then
    echo "Aborting commit. Your commit message is invalid." >&2
    exit 1
fi
if ! head -1 "$1" | grep -qE "^.{1,88}$"; then
    echo "Aborting commit. Your commit message is too long." >&2
    exit 1
fi
```

In order to simplify the process of making a commit according to conventional commit standards, you can install [Commitizen](https://commitizen-tools.github.io/commitizen/).

Install commitizen as a dev dependency,

```bash
npm i –save-dev commitizen
```

Then initialize commitizen,

```bash
commitizen init cz-conventional-changelog --save --force
```

This would provide a setup such that when you make a commit(after `git add …` of course) using the command,

```bash
git cz
```

You get this,

![Commitizen cli](https://cdn.hashnode.com/res/hashnode/image/upload/v1645109039135/YCq7m9O8t.png)

Now you’ve set up an automated workflow with husky, lint-staged, eslint, prettier and commitizen.

>This implementation can be extended using [dependency cruiser](https://www.npmjs.com/package/dependency-cruiser) to lock down certain dependencies from being used across the codebase. This is however quite optional and should be adopted as the need demands.


## Caveats

There are some caveats to this approach though.

- Might be overkill for small apps
- Doesn’t eliminate the need for proper communication
- Not a replacement for CI


## Conclusion

Compliance with coding standards leads to more maintainable software and a team that works well better and ships faster. This is as a result of less back and forth on pull requests.

A [research article](https://www.researchgate.net/publication/328912784_The_Benefits_of_the_Coding_Standards_Enforcement_and_its_Impact_on_the_Developers_Coding_Behaviour-A_Case_Study_on_Two_Small_Projects) that studied two small projects even shows a dropping error rate when coding standards are adopted.

Its authors' quote,

>The dropping of error trends indicates that as developers align  with  the  coding  standard,  there  will  be  less  fault corrections,  hence  fewer  probability  to  new  faults. Nevetheless  although  less,  developers  will  be  making errors  in  any  circumstances,  which  justifies  the  coding standard check step in  the software development process. Another thing that  is evident through this research is that the  use  of  checking  tools  in  the  implementation  step mitigates the errors in the code checking step.

The adoption of coding standards can lead to better performance from the team generally as well as boost individual performance and growth. It provides a focus on reliability, security, and structure.

Consequently, it dampens individual coding style yet I argue that priority should be placed on **structure over style and consistency over comfort**. In my view, its benefits far outweigh its cost.

Hope this article helps.


## Resources

1. https://www.youtube.com/watch?v=oWty0Nw1ydk&t=486s&ab_channel=LeighHalliday
2. https://www.youtube.com/watch?v=jNxDNoYEGVU&t=1220s&ab_channel=LeoRoese
3. https://githooks.com/
4. https://github.com/aitemr/awesome-git-hooks
5. https://www.researchgate.net/publication/328912784_The_Benefits_of_the_Coding_Standards_Enforcement_and_its_Impact_on_the_Developers_Coding_Behaviour-A_Case_Study_on_Two_Small_Projects
6. https://medium.com/docon/airbnb-javascript-style-guide-key-takeaways-ffd0370c053
7. https://taiyr.me/what-is-the-difference-between-code-linters-and-formatters
