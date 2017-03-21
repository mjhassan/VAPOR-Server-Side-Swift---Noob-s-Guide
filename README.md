# VAPOR: Server Side Swift - Noob's Guide

Well, if you end up here I think you are interested in server side Swift, specially VAPOR.<br/> 
Swift is a beautiful language and VAPOR is it's perfect company at server side. Since Swift v2.2 became open source and
Linux compatible at the end of 2015, server side Swift has been on of the active development scope. There are number
of web framework written in Swift, including [Perfect](https://github.com/PerfectlySoft/Perfect), 
[Vapor](https://github.com/vapor/vapor), [Kitura](https://github.com/IBM-Swift/Kitura), [Zewo](https://github.com/Zewo/Zewo).
Among those VAPOR is most simple. In this post we will learn how to write server API using VAPOR from soup to nuts.<br/><br/>

Vapor is a web framework, developed by the collaborators from Qutheory, which outstands for its simplicity, type safety and speed.

<h1>Installation and configuration of Vapor</h1>
Before we start with Vapor we need few things configured.<br/>
First, we need is Swift 3 or later, which is obvious. If you are in macOS you should already have Xcode 8 or later. If not, Install [Xcode 8](https://itunes.apple.com/us/app/xcode/id497799835?mt=12) from the Mac App Store or using [.xip file](https://developer.apple.com/services-account/download?path=/Developer_Tools/Xcode_8.2.1/Xcode_8.2.1.xip). Xcode comes with Swift compiler. By the time of writing this post, Xcode version is 8.2.1 and Swift 3.0.2. 
<br/>
Swift installation in Ubuntu is also easy. Type the following command in terminal:

    curl -sL swift.vapor.sh/ubuntu | bash
If you want to install manually follow [this process](https://vapor.github.io/documentation/getting-started/install-swift-3-ubuntu.html).<br/>

Now, to check if your system is ready for Vapor, run the following command in Terminal:

    curl -sL check.vapor.sh | bash
If everything is correct, intall Vapor using this command:

    curl -sL toolbox.vapor.sh | bash
    
When installation is done you will see Vapor's command line interface, which provides shortcuts and assistance for common tasks.
![Vapor-cli.png](https://cloud.githubusercontent.com/assets/1342803/17454691/97e549e2-5b6d-11e6-979a-f0cd6b6f1b0a.png)

Make sure the Toolbox installed successfully by running the help query. You should see a print out of the available commands. You can run the `--help` option on any Toolbox command.

    vapor --help
    
