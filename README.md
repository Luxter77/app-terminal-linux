# Windows Terminal Linux Port
<!-- ![Windows Terminal project logos and branding image](https://github.com/microsoft/terminal/assets/91625426/333ddc76-8ab2-4eb4-a8c0-4d7b953b1179) -->
<!-- Something linux at some point -->

<!-- Build status removed from here, TODO add at some point in the future when we have something that builds in the first place. -->

Based on Microsoft's [Windows Terminal](https://github.com/microsoft/terminal)

This repository contains the source code for:

- Windows Terminal
- Windows Terminal Preview
- The Windows console host (`conhost.exe`)
- Components shared between the two projects
- [ColorTool](./src/tools/ColorTool)
- [Sample projects](./samples)
  that show how to consume the Windows Console APIs

Related repositories include:

- [Windows Terminal](https://github.com/microsoft/terminal)
- [Windows Terminal Documentation](https://learn.microsoft.com/windows/terminal)
  ([Repo: Contribute to the docs](https://github.com/MicrosoftDocs/terminal))
- [Console API Documentation](https://github.com/MicrosoftDocs/Console-Docs)
- [Cascadia Code Font](https://github.com/Microsoft/Cascadia-Code)

## Terminal & Console Overview

Please take a few minutes to review the overview below before diving into the
code:

### Windows Terminal

Windows Terminal is a new, modern, feature-rich, productive terminal application
for command-line users. It includes many of the features most frequently
requested by the Windows command-line community including support for tabs, rich
text, globalization, configurability, theming & styling, and more.

The Terminal will also need to meet our goals and measures to ensure it remains
fast and efficient, and doesn't consume vast amounts of memory or power.

### The Windows Console Host

The Windows Console host, `conhost.exe`, is Windows' original command-line user
experience. It also hosts Windows' command-line infrastructure and the Windows
Console API server, input engine, rendering engine, user preferences, etc. The
console host code in this repository is the actual source from which the
`conhost.exe` in Windows itself is built.

Since taking ownership of the Windows command-line in 2014, the team added
several new features to the Console, including background transparency,
line-based selection, support for [ANSI / Virtual Terminal
sequences](https://en.wikipedia.org/wiki/ANSI_escape_code), [24-bit
color](https://devblogs.microsoft.com/commandline/24-bit-color-in-the-windows-console/),
a [Pseudoconsole
("ConPTY")](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/),
and more.

However, because Windows Console's primary goal is to maintain backward
compatibility, we have been unable to add many of the features the community
(and the team) have been wanting for the last several years including tabs,
unicode text, and emoji.

These limitations led us to create the new Windows Terminal.

> You can read more about the evolution of the command-line in general, and the
> Windows command-line specifically in [this accompanying series of blog
> posts](https://devblogs.microsoft.com/commandline/windows-command-line-backgrounder/)
> on the Command-Line team's blog.

### Shared Components

While overhauling Windows Console, we modernized its codebase considerably,
cleanly separating logical entities into modules and classes, introduced some
key extensibility points, replaced several old, home-grown collections and
containers with safer, more efficient [STL
containers](https://docs.microsoft.com/en-us/cpp/standard-library/stl-containers?view=vs-2022),
and made the code simpler and safer by using Microsoft's [Windows Implementation
Libraries - WIL](https://github.com/Microsoft/wil).

This overhaul resulted in several of Console's key components being available
for re-use in any terminal implementation on Windows. These components include a
new DirectWrite-based text layout and rendering engine, a text buffer capable of
storing both UTF-16 and UTF-8, a VT parser/emitter, and more.

### Creating the new Windows Terminal

When we started planning the new Windows Terminal application, we explored and
evaluated several approaches and technology stacks. We ultimately decided that
our goals would be best met by continuing our investment in our C++ codebase,
which would allow us to reuse several of the aforementioned modernized
components in both the existing Console and the new Terminal. Further, we
realized that this would allow us to build much of the Terminal's core itself as
a reusable UI control that others can incorporate into their own applications.

## Contributing

We are excited to work alongside you, our amazing community, to build and
enhance Windows Terminal\!

### Coding Guidance

Please review these brief docs below about our coding practices.

This is a work in progress as we learn what we'll need to provide people in order to be effective contributors to our project.

- [Coding Style](./doc/STYLE.md)
- [Code Organization](./doc/ORGANIZATION.md)
- [Exceptions in our legacy codebase](./doc/EXCEPTIONS.md)
- [Helpful smart pointers and macros for interfacing with Windows in WIL](./doc/WIL.md)
