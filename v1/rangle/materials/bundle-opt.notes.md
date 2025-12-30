Bundle-analyzer and performance article outline/ notes
overview
● Explain the importance of optimizing an application's performance
○ larger bundle size can significantly increase page load times
● Introduce the concept of bundle size and its impact on page load times
○ The size of your js that needs to be loaded in the browser, the larger the bundle the
longer your page will take to load
○ Chunking
○ Code splitting
○ Tree shaking
● Problems / Pitfalls. what are we looking to fix. what can we improve.
○ Duplicates (2 versions of same package)
○ Unused stuff (not tree shaken)
● Solutions
● T ools and approaches. how to improve
Intro:
● Explain the importance of optimizing an application's performance
○ larger bundle size can significantly increase page load times
● Introduce the concept of bundle size and its impact on page load times
○ The size of your js that needs to be loaded in the browser, the larger the bundle the
longer your page will take to load
○ Chunking
● Briefly introduce the tools that will be used in the tutorial
○ Brief intro about webpack and its role
■ Webpack is a JS module bundler that complies, transforms and packages
your application’s source code, along with its dependencies, into output
files that can be loaded in your browser
■ https://webpack.js.org/concepts/
■ vite? alternatives to webpack.
■ this still applies to next. this means almost 100% of cases
○ How it knows how to bundle things (imports, exports)
■ show the output, without uglify. u can actually see the bundle objects. you
could color coat.
○ Webpack Bundle Analyzer(
https://www.npmjs.com/package/webpack-bundle-analyzer)
○ This will generate a visualization of your application's bundle
○ Webpack Bundle Analyzer is a powerful tool that provides you with a visual
representation of your JS bundle size, making it easier to identify areas for
optimization
○ It can show your larger dependencies, duplicated modules and unused modules
that may be able to be removed to reduce your bundle size
○ we load some subset of the chunks. not sure how this is relevant
● Install the Webpack Bundle Analyzer package in your project
○ Add some code snippets to show this
● Interpreting the results of the visualization
○ An interactive treemap is generated and this represents the size and structure of
your JS bundle
○ Organized into nested rectangles which each represent a module or dependency
○ The size of each rectangle corresponds to the overall size of the module in the
bundle, larger rectangle = larger modules
○ The hierarchy and grouping helps you understand the overall structure of your
project and how modules are related to each other
○ Hovering over a module will show a tooltip that gives you more info like size, name
and path for each module
○ Using the search feature on the left side allows you to search for specific modules
and can be useful, especially when trying to see if I module has been successfully
removed from your project
● Statoscope (https://statoscope.tech/)
● Once you have used Webpack to create a stats.json file, you can drop that file into the
Statoscope tool and it will analyze it for you and create a report
● Where the webpack bundle analyzer helps you identify which modules may be large,
duplicated or unused, it doesn’t give as clear a picture as to where (why?) these are being
used (included?)
● Statoscope can help in finding where certain modules are used (imported?) to help you
safely remove them
● Statoscope is a webpack stats analyzer
○ You can examine details about your projects individual modules, including their
size, dependencies, and location within the codebase (screenshot or something, i
dont fully understand what you mean by “location”)
○ This report gives you a lot of information and insight as to the size of bundles,
chunks and assets in your codebase
○ The section I found the most useful was the Entrypoints -> Modules -> clicking into
the module I was trying to remove, looking at the Reasons -> Issuer Path
○ The Reasons can include explicit import statements in your code, dynamic imports,
or dependencies requires by another module
○ The Issuer Path shows the chain of modules that led to the inclusion of a specific
module, it’s essentially a list of parent modules that required or imported the
module we’re looking for
○ It helps you trace back to the root entry that caused the inclusion of the specified
module
● Below is an example of the output from Statoscope where you can transverse through the
modules and where they are loaded
● Interpreting the report to see where your modules are being loaded
○ Removing the desired modules from the pages it’s loaded on
● Re-running webpack-bundle-analyzer and Statoscope to verify these changes and
improvements
○ in a video this would be straight forward. i would like to know the process and
thinking that you do to arrive at “hypotheses” / “things to try” and then verify.
obviously there are many ways, just walk us through your method.
● SVGator (honourable mention?)
○ icons tend to be one of the heaviest dependency packages. you dont use that many
of them
○ additional visualizations for presentation?
● Summarize the benefits of analyzing and optimizing loaded modules
● Encourage developers to continuously monitor and optimize their applications
○ automated tools for this? part of pipeline. you have to explicitly increase size
restrictions if you need it. like a “debt ceiling”