# G1ANT.Robot Tutorials

Welcome to the open source [tutorials](https://learning.g1ant.com) for [G1ANT.Robot](https://www.g1ant.com/). Please review this README file to understand how you can assist in contributing to the G1ANT.Robot tutorials.

## Getting Started

Contributing to open source is more than just providing updates, it's also letting us know when there is an issue. You can submit issues with the standard [Issues](https://help.github.com/articles/about-issues/) tab on GitHub.

### Prerequisites

Contributing to the documentation requires a GitHub account and some [Markdown](https://guides.github.com/features/mastering-markdown/) knowledge.

### Conventions

Folders are treated as separated courses in the Tutorials. Folder names are used for the titles of courses, so [For Beginners](../For Beginners/) folder will turn into “For Beginners” course title on the website.

Files represent individual lessons within a course. The filenames are sequential numbers determining the lessons order. We start with 10 and use the increments of 10 for the filenames, so that there is some room left for additional intermediate lessons that might appear in future and could be placed between existing ones without disturbing the whole file structure and the resulting lessons order in the Tutorials.

We use [headers](https://guides.github.com/features/mastering-markdown/#examples) in Markdown files to allow navigation in the Tutorials structure. Each lesson’s title is derived from header 1 in the .md file.

In tutorials, we avoid media objects (pictures, videos and so on), because they would affect displaying the content in the G1ANT.Robot panel. Should you want to attach any example file for your tutorials, place it in [-assets](../-assets/) folder, and link to it as relative path in the .md file, for example `../-assets/data.xslx`. 

Folders and files with the “-” prefix are skipped by our sync tool, which gathers together Markdown files from [Manual](https://github.com/G1ANT-Robot/G1ANT.Manual), Tutorials and [Addon](https://github.com/G1ANT-Robot/G1ANT.Addon) repositories and creates content to be displayed on the [G1ANT.Manual](https://manual.g1ant.com) and [G1ANT.Learning](http://learning.g1ant.com) websites.

## Contributing

Please read [CONTRIBUTING](CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## License

Please refer to [LICENSE](LICENSE) file for all Licensing information.

