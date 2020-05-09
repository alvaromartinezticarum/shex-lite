<img src="/doc/assets/shex-lite-full-logo.png" alt="Shex-lite logo" height="70">

# Shape Expression Lite Language

|                    | **Master** |
|--------------------|------------|
|**ShEx Lite CI**|![ShEx-Lite CI](https://github.com/weso/shex-lite/workflows/ShEx-Lite%20CI/badge.svg?branch=master)|
|**AWS CI**|[![Build Status](https://codebuild.us-east-1.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoiRUE1M2VkRUhxa01WdWphR3Q5eW9GN3gvZExpTnlQNTJUci9wNUR3cU9DbXBFMXREcnZ4UU9NR3dWeEZpNHhxZGdaem84NHJyOUx0ekdWcG5ON215a1A4PSIsIml2UGFyYW1ldGVyU3BlYyI6IitKbnZwL094R1ZhWDZCQm8iLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=master)](https://console.aws.amazon.com/codesuite/codebuild/projects/shex-lite/history?region=us-east-1)|
|**Code Coverage**|[![codecov.io](https://codecov.io/github/weso/shex-lite/coverage.svg?branch=master)](https://codecov.io/github/weso/shex-lite?branch=master)|

## Welcome to ShEx Lite
ShEx Lite is a lightweight version of [ShEx](https://github.com/weso/shex-s) that has as an aim reduce the complexity of the syntax, improve the semactic analisis of the schemas and boost the performance of the validation process.

One of the restrictions of the language is that it represents a subset of ShEx. Therefore any source code developed in shex-lite format will be completly compatible with ShEx implementations. But although it is inspired in those ShEx implementations it is a complete independent language, it has its own syntax, semantics, features, compiler and validation process.

To learn more about the language, visit [shex-lite.org](https://shex-lite.org).

## Compiler Architecture
As a whole, the ShEx-Lite compiler is principally responsible for translating Shex-Lite source code into dofferent intermediate representations like Java, Python or HTML. However, the Shex-Lite compiler front-end is ready for integration with other tools like IDE and syntax coloring thanks to its API design inspired in modern compilers like Roslyn, SwiftC or RustC.

Mainly the compiler is build in 5 major stages:
<img src="/doc/assets/shex-lite-arch-reduced.png" alt="Shex-lite Arch">

1. The source code is translated in to a Syntax Tree, that is a tree that contains all the tokens generated by the lexer in a tree structure generated from the rules of the grammar.

2. The Syntax Tre is parsed again to remove all unneed tokens like semicolons, braces and parenthesis. That way the Abstract Syntax Tree is formed.

3. Fom the AST we apply the semantic analysis and transformations to transform the tree in to a graph that is called the Shex-lite Intermediate Language. This graph contains information like where a definition took place and adds all of those information to other nodes.

4. Once we have the Intermediate Language we perform an analysis to validate that it is consistent. There is no missing references and things like that.

5. Finally the compiler generates the code for the different intermediate representations.

To look deeper to the compiler the following picture illustrates perfectly the data-flow:
<img src="/doc/assets/shex-lite-arch-full.png" alt="Shex-lite Arch">

## Contributing to ShEx Lite
Contributions to ShEx Lite are welcomed and encouraged! Please see the [Contributing to ShEx Lite guide](https://shex-lite.org/contributing/).

To be a truly great community, [shex-lite.org](https://shex-lite.org/) needs to welcome developers from all walks of life, with different backgrounds, and with a wide range of experience. A diverse and friendly community will have more great ideas, more unique perspectives, and produce more great code. We will work diligently to make the ShEx Lite community welcoming to everyone.

To give clarity of what is expected of our members, ShEx Lite has adopted the code of conduct defined by the Contributor Covenant. This document is used across many open source communities, and we think it articulates our values well. For more, see the [Code of Conduct](https://shex-lite.org/community/#code-of-conduct).

### Proposals
If you want to contribute to ShEx-Lite the best and fastest way is to submit a proposal about a change that you would like to integrate with the project. For example: If you find that would be interesting to add a new SIL Generator for a language just submit a proposal with your idea and listen for the feedback of the core team and the comunity. We love to have proposals.

To submit your proposal we encourage you to use the [GitHub issues](https://github.com/weso/shex-lite/issues) system. You just have to click on create new issue and select the proposal template. And don't worry, if something is not up to the standards we will contact you in order to try to find a solution.

### Roadmap
Shex-lite is a project that always maintains a minimum view of one year onwards, in this way we can anticipate different demands from users. Currently our roadmap is hold here [[SLI-0090] 🚀 Long Term Roadmap (LTR)](https://github.com/weso/shex-lite/issues/90).

## Getting Started
These instructions give the most direct path to a working ShEx Lite development environment. To build from source you will need about 2Gb of disk space for sources. Depending on your machine, a clean build can take a few minutes. Naturally, incremental builds are much faster.

### System Requirements
ShEx Lite is developed using scala PL and compiles against the JVM. Therefore all JVM supported systems are currently supported as host development operating system.

#### Scala
The compiler of ShEx Lite is build using scala language, that means that you will need to install [Scala](https://github.com/scala/scala) in order to be able to compile the sources.

> Currently ShEx Lite uses scala 2.13.1.

#### IntelliJ IDEA
We also encourage you to use the IDE [IntelliJ](https://www.jetbrains.com/es-es/idea/). ShEx Lite was developed using this IDE and already includes some directives in the sbt to ensure that the project is imported and set up correctly.

### Getting Sources for ShEx Lite
First create a directory for all ShEx Lite sources:
```bash
mkdir shex-lite-sources
cd shex-lite-sources
```
Cloning the repository containing the sources:
```bash
git clone https://github.com/weso/shex-lite.git .
```

## Building ShEx Lite
ShEx-Lite uses SBT and scala. So build the project is as easy as go to the root directory of the project and execute:
```bash
sbt assembly
```

## Testing ShEx Lite
We encourage you to add as much tests as possible and then run the previous existing ones with your new tests. As more tests we can do more confident about its behaviour that we will be. In the folder `test` you will find all resources that might be need.

In order to execute all tests locally you will need SBT. Again, testing is super easy and doesn't take too long. You just have to execute:
```bash
sbt test
```

## Learning More
Be sure to look through the [docs](https://github.com/weso/shex-lite/tree/master/doc) directory for more information about the compiler. In particular, the documents titled [Debugging the ShEx Lite Compiler](doc/DebuggingTheCompiler.bs) and [Continuous Integration for ShEx Lite](doc/ContinuousIntegration.bs) are very helpful to understand before submitting your first PR.

### Building Documentation
To read the compiler documentation, start by installing the [Bikeshed](https://github.com/tabatkins/bikeshed) documentation generator tool by runing the command:
```bash
git clone https://github.com/tabatkins/bikeshed.git
pip install --editable $PWD/bikeshed
bikeshed update
```
Once complete, you can build the ShEx Lite documentation by changing directory into [docs](https://github.com/weso/shex-lite/tree/master/doc) and typing `./scripts/build-doc.sh`. This compiles the `.bs` files in the [docs](https://github.com/weso/shex-lite/tree/master/doc) directory into HTML in the `doc` directory.

Many of the docs are out of date, but you can see some historical design
documents in the `doc` directory.

## Authors

- **Guillermo Facundo Colunga** - *Initial work* - [thewilly](https://github.com/thewilly)
- **Alejandro González Hevia** - *Core Team* - [alejgh](https://github.com/alejgh)
- **Jose Emilio Labra Gayo** - *Core Team* - [labra](https://github.com/labra)
- **Daniel Fernández Álvarez** - *Core Team* - [danifdezalvarez](https://github.com/DaniFdezAlvarez)

See also the list of [contributors](https://github.com/weso/shex-lite/graphs/contributors) who participated in this project.

## Collaborations
The project is completely open source and therefore they accept collaborations from different projects from all over the world including:

### [Hércules - ASIO (University of Murcia)](https://www.um.es/web/hercules/)
<img src="/doc/assets/logos_feder.jpg" alt="Shex-lite logo" height="90"><img src="/doc/assets/hercules-crue.jpg" alt="Shex-lite logo" height="90">

The Hercules ASIO project focuses on creating an ontological infrastructure and a semantic architecture to manage the administration of research in the environment of Spanish research centers and universities.

> _The HERCULES-Semantics of University Research Data project has a budget of Five Million Four Hundred Sixty Two Thousand Six Hundred Euros with an ERDF co-financing of 80%, therefore the European Regional Development Fund (ERDF), through the then Ministry of Economy, Industry and Competitiveness (currently the Ministry of Science and Innovation) as the Intermediate Body of the ERDF Smart Growth Operational Program - POCint (now the Multi-regional Operational Program of Spain - POPE) makes a contribution of Four Million Three Hundred Seventy Thousand Eighty euros._


## License

ShEx Lite is primarily distributed under the terms of both the MIT license and the GNU General Public License (Version 3.0), with portions covered by various licenses.

See [LICENSE-MIT](LICENSE-MIT), [LICENSE-GNU](LICENSE-GNU), and [LICENSE](LICENSE) for details.

## Trademark
The ShEx Lite language is an open source, community project governed by a core team. It is also sponsored by the Web Semantics Oviedo Research Group at University of Oviedo ("WESO"), which owns and protects the ShEx Lite trademark and logo.

If you want to use these names or brands, please read the media guide.

Third-party logos may be subject to third-party copyrights and trademarks. See Licenses for details.
