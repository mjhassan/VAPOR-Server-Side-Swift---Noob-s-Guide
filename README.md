# Vapor: Server Side Swift - Noob's Guide

Well, if you end up here I think you are interested in server side Swift, specially Vapor.<br/> 
Swift is a beautiful language and Vapor is it's perfect company at server side. Since Swift v2.2 became open source and
Linux compatible at the end of 2015, server side Swift has been on of the active development scope. There are number
of web framework written in Swift, including [Perfect](https://github.com/PerfectlySoft/Perfect), 
[Vapor](https://github.com/vapor/vapor), [Kitura](https://github.com/IBM-Swift/Kitura) and [Zewo](https://github.com/Zewo/Zewo).
Among those Vapor is most simple. In this post we will learn how to write server API using Vapor from soup to nuts.<br/><br/>

Vapor is a web framework, developed by the collaborators from Qutheory, which outstands for its simplicity, type safety and speed.

<h2>Installation and configuration of Vapor</h2>
Before we start with Vapor we need few things configured.<br/>
First, we need is Swift 3 or later, which is obvious. If you are in macOS you should already have Xcode 8 or later. If not, Install Xcode 8 from Mac AppStore (https://goo.gl/oqBK0f) or using .xip file from https://goo.gl/wvH864. Xcode comes with Swift compiler. By the time of writing this post, Xcode version is 8.2.1 and Swift 3.0.2. 
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
    
<h2>Create and run a Vapor server</h2>
Vapor comes with default server template. Create a basic server, using CLI, with simple command.

    vapor new ServerExample
A server template project, named ***ServerExample*** will be created. Enter into the project folder using

    cd ServerExample
The folder structure of the project will probably look like:

ServerExample<br/>
├── Sources<br/>
│   └── App<br/>
│       └── Controllers<br/>
│       └── Middleware<br/>
│       └── Models<br/>
│       └── main.swift<br/>
├── Public<br/>
├── Resources<br/>
│   └── Views<br/>
└── Package.swift<br/>

Our main focus will be on the `main.swift` file.<br/><br/>

Now `build` and `run` the server with simple commands.

    vapor build
    vapor run
You will see `Server 'default' starting at 0.0.0.0:8080` in the terminal output. If you visit `0.0.0.0:8080`, `127.0.0.1:8080` or [localhost:8080](http://localhost:8080/) you should see that “it works”:
![vapor.png](https://github.com/mjhassan/VAPOR-Server-Side-Swift---Noob-s-Guide/blob/master/vapor.png)

Let's check some code, open the `main.swift` file using your favorite text editor. Mac user can use Xcode for editing, build and run the Vapor project. Simply, type `vapor xcode` in your terminal. Output will be:

    Fetching Dependencies [Done]
    Generating Xcode Project [Done]
    Select the `App` scheme to run.
    Open Xcode project?
    y/n>
type **y** and press enter. ***ServerExample*** project will open in Xcode. Now, in `main.swift` you will see following codes:

    import Vapor
 
    let drop = Droplet()
 
    drop.get { req in
        return try drop.view.make("welcome", [
                "message": drop.localization[req.lang, "welcome", "title"]
        ])
    }
     
    drop.resource("posts", PostController())
     
    drop.run()

Let's explain the code a bit.

    import Vapor
This standerd _import delaration_ of Vapor, which let you access functionalities and symbols defined in Vapor.

    let drop = Droplet()
The `Droplet` is a service container that gives you access to many of Vapor's facilities. It is responsible for registering routes, starting the server, appending middleware, and more. The `Droplet` class has a plethora of useful functions on it, and is used extensively.

    drop.get
`get` method creates a Vapor's Router using `Droplet`, which handles a GET request.

    return try drop.view.make
 `drop.view.make` creates the view and `return` provides the response when you go to localhost:8080. As it may cause exception if it is not found, hence `try` keyword.
 
     drop.resource
This one gets resource from _PostController_ and registered into the router as a RESTful resource.

And lastly, `drop.run()` runs the server and listening to the port 8080. This port is defined in `servers.json` file, which is inside _Config_ folder.
