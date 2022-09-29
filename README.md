# GSoC 2022 - Scalafix Final Submission

## Project Details

|                        |                                                                                                                                                                            |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Project name           | Porting of Scalafix ExplicitResultTypes rule to Scala 3                                                                                                                    |
| Organization           | [Scala Center](https://summerofcode.withgoogle.com/programs/2022/organizations/scala-center), [Scala Center Official Site](https://scala.epfl.ch/)                         |
| Scala Center idea link | [Project proposal link](https://github.com/scalacenter/GoogleSummerOfCode2022#adapt-the-explicitresulttypes-scalafix-rule-for-scala-3)                                     |
| Github Issues          | [ExplicitResultType issue](https://github.com/scalacenter/scalafix/issues/1583), [Scalafix cross compiled to scala-3](https://github.com/scalacenter/scalafix/issues/1316) |
| Project links          | [Scalafix Github repo](https://github.com/scalacenter/scalafix), [Scalafix website](https://scalacenter.github.io/scalafix/)                                               |
| Mentors                | [Brice Jaglin](https://github.com/bjaglin), [Meriam Lachkar](https://github.com/mlachkar)                                                                                  |
| Contributor            | [Razvan Vacaru](https://www.linkedin.com/in/razvan-vacaru-17787b5a)                                                                                                        |
| GSoC Proposal          | [GSoC Link](https://summerofcode.withgoogle.com/programs/2022/projects/gQ08FcXb)                                                                                           |

## Scalafix 

Scalafix is a linting, code completion, rewriting tool for scala codebases. The Scalafix
tool can be used as a CLI from Terminal, as part of your build with 
[Maven](https://github.com/evis/scalafix-maven-plugin) or [SBT](https://github.com/scalacenter/sbt-scalafix),
and as part of your CICD pipelines.

[Scalafix](https://docs.scala-lang.org/scala3/guides/migration/tooling-tour.html#scalafix) is part of the 
set of migration tools which will make it easier to migrate Scala code to Scala 3.

## Benefits to the Community

The reasons why porting Scalafix and ExplicitResultTypes to Scala 3 are:
- Linting and re-writing code capabilities will be available for Scala 3 projects
  - More readability, better developer experience, better maintainability of Scala3 projects  
- Scalafix rules written in Scala 3 will be compatible and compilable 
- Scalafix helps migrating code between Scala 2 and Scala 3 versions

## Status before the GSoC project

Scalafix currently build in Scala versions 2.11, 2.12 and 2.13 . It relies on the Scala 2 compiler for:
- The [ExplicitResultTypes Rule](https://scalacenter.github.io/scalafix/docs/rules/ExplicitResultTypes.html), 
  where code is compiled in order to infer the Types of the members
- The [Custom / External Rules](https://scalacenter.github.io/scalafix/docs/developers/tutorial.html) compilation

Since Scalafix uses the Scala compiler, porting Scalafix or ExplicitResultTypes to Scala 3 also means 
reimplementing compilation logic in scalafix using the new [Scala 3 Dotty compiler](https://index.scala-lang.org/lampepfl/dotty)

## Work Done 

A list of Pull requests, or commits, of the work done in chronological order:

- To familiarize with the Scalafix codebase, I picked up a bug related to ExplicitResultTypes:
  - [Fixed ExplicitResultTypes for implicit members with config](https://github.com/scalacenter/scalafix/issues/1216), [PR Link](https://github.com/scalacenter/scalafix/pull/1627)
- [Scalafix-core module cross compiled in Scala 3](https://github.com/scalacenter/scalafix/issues/1316#issuecomment-1185515566), [PR Link](https://github.com/scalacenter/scalafix/pull/1629)
- [Ask Mill-Scalafix maintainers to release with Scalafix 0.10.0](https://github.com/joan38/mill-scalafix/pull/91#issuecomment-1178675781)
- [Scalafix-rules module cross compiled in Scala 3](https://github.com/scalacenter/scalafix/pull/1643)
- [Update Unit module Scalatest version to 3.2.13](https://github.com/scalacenter/scalafix/pull/1661)
- [RuleCompiler using dotty compiler, for Scala 3 compilation](https://github.com/scalacenter/scalafix/pull/1650/files#diff-fdc2359988794371ab0f9ef79b3204495b197cbff15dd4d84123edf8c512c4c2)
- [(WIP) Scalafix-Reflect + Scalafix-cli + Test modules cross compiled to Scala 3](https://github.com/scalacenter/scalafix/pull/1650)
  - (Done) [Squashed commits: Scalafix-reflect3 cross compiled for Scala 3](https://github.com/scalacenter/scalafix/pull/1650/commits/6c35519958a628f1a629a19892f4d816f55d12f1)
  - (Done) [Squashed commits: Scalafix-cli3 cross compiled for Scala 3](https://github.com/scalacenter/scalafix/pull/1650/commits/390b84888fa90e2614beb0cda80cdc31bdca8429)
  - (Done) [Squashed commits: Scalafix-testkit3 cross compiled for Scala 3](https://github.com/scalacenter/scalafix/pull/1650/commits/e08e1cb975b77e6b8d432211902471aa11349f48)
  - (WIP) Unit module test fixes, RuleCompiler fixes, minor refactoring to code or sbt build, see [commits](https://github.com/scalacenter/scalafix/pull/1650/commits)

## Useful resources

A list of web resources used while working on the project: 

- [Scalameta Types](https://scalameta.org/docs/trees/quasiquotes.html#types-metatype)
- [Scalameta Trees](https://scalameta.org/docs/trees/guide.html#what-is-a-syntax-tree)
- [AST Explorer](https://astexplorer.net/#/gist/ec56167ffafb20cbd8d68f24a37043a9/677e43f3adb93db8513dbe4e2c868dd4f78df4b3)
- [Dotty usage in Github](https://github.com/search?q=org%3Alampepfl+import+dotty.tools.dotc.Compiler&type=code)
- [Dotty internal documentation](https://dotty.epfl.ch/docs/internals/overall-structure.html)


## Remaining work - Next steps

The Project is unfortunately not finished even given a project extension from the regular 12 weeks length.
These are the task still to be done:

- Finish the cross compilation of Scalafix to Scala 3
  - In particular fixing unit tests `ScalafixArgumentsSuite` and `ScalafixImplSuite`
- Publishing a new Scalafix version, without ExplicitResultTypes
- Implement ExplicitResultTypes using the dotty compiler
- Unit test and documentation

## Scalafix Community 

From time to time I have asked for help or advice to the community:
- Scala Center Discord channel - https://discord.com/invite/scala
- Scalameta Discord channel - https://discord.com/invite/RFpSVth
- Scalafix Gitter channel - https://gitter.im/scalacenter/scalafix
  - This will soon be archived in favor of the new channel on the Scalameta Discord

(Thanks to everyone in the above chatrooms who helped and replied to my questions!)
