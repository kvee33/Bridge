﻿**Please note**

**Bridge.PostBuild** (the project that triggers Bridge Core JavaScript generation) should be a Bridge project (`NoStdLib` etc).
This forces the project recompilation when compiler tests **Bridge.Translator.Tests** are run with NUnit Test Adapter.
NUnit Test Adapter run test discovery even if the solution if fully rebuilt already.
The test discovery process "does not like" `NoStdLib` projects (earlier Test Adapter version even shown exceptions in Test Output window).
Therefore the discovery process always tries to rebuild `NoStdLib` projects. We did not find a way to suppress test discovery for certain projects.
In order to force the process to do it (discovery) properly (considering project dependencies) the **Bridge.PostBuild** should also be a `NoStdLib` project.
So that it will be built each time the test discovery process touches **Bridge** and **Bridge.Html5** projects.