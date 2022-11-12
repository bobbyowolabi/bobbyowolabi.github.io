---
layout: post
title: Building Netty Source Code on Mac
image: /img/netty.png
description: null
comments: true
published: true
---

> Netty is an asynchronous event-driven network application framework for rapid development of maintainable high performance protocol servers & clients.<sup>[[1]](#netty-documentation)</sup>  


Netty is used in the [core infrastructure at major organizations][netty-adopters] including Twitter<sup>[[a]](#netty-at-twitter)</sup> & Netflix<sup>[[b]](#netty-at-netflix)</sup> .

[**[Netty Developer Guide Steps to Build the Source Code]**][build-steps]

There were some modifications I needed to make when using the above guide to get the code to build successfully.


# Steps

These are the steps I used to build it on a mac.

1. **Install the Java 11 JDK** <sup>[[c]](#why-netty-needs-java11)</sup>. <br/>
	This can be downloaded from [Oracle][oracle-jdk] or number of other vendors as listed in the developer guide.

	I downloaded the `x64 DMG Installer` and went through the prompts.

	I recommend updating your `.bash_profile`<sup>[[d]](#bash-profile)</sup> file to automatically set your `JAVA_HOME` environment variable.
	
	Add the following anywhere in the file:
	```bash
		alias setJdk11='export JAVA_HOME=$(/usr/libexec/java_home -v 11)'
		setJdk11
	```

1. **Install [Maven][maven]**  <br/>
	I had maven version 3.5.3 installed (Apache Maven 3.8.6 is the latest release).

1. **Install [Git][git]** <br/>
	Not necessary to build, but needed to commit and contribute code changes.

	> "if using MacOS, when you commit code, CRLF will be automatically converted to LF" by setting the following property:
	```bash
	git config --global core.autocrlf input
	```

1. **Install Additional Listed Packages** <br/>
	```bash
	brew install autoconf automake libtool openssl
	```
	These are some packages listed in the guide to install.

1. **Install Apple Command Line Tools**<sup>[[e]](#command-line-tools-note)</sup> <br/>
	```bash
	xcode-select --install
	```

1. **Build the Source!** <br/>	
	Run the following command in the base soure code directory.
	```bash
	./mvnw clean install -DskipTests -T1C
	```

	If successful, the following will be printed.
	```bash
	[INFO] ------------------------------------------------------------------------
	[INFO] BUILD SUCCESS
	[INFO] ------------------------------------------------------------------------
	[INFO] Total time:  02:36 min (Wall Clock)
	[INFO] Finished at: 2022-11-12T00:31:11-08:00
	[INFO] ------------------------------------------------------------------------
	```

# What I Didn't Do
Because I got a few build errors in the `netty5-transport-native-unix-common` module, I immedaitely thought I had to go through the steps in the sectipon of the developer guide entitled ["Building the native transports"][build-native-transports].  It turns out that it was not necessary; however, it confused me a bit.


### References
[<a name="netty-documentation">1</a>] *Various Authors*. [“Netty: Home.”][netty] The Netty Project, 2022, [URL][netty].

[<a name="netty-at-twitter-with-finagle">2</a>] *Author Unknown*. “Netty at Twitter with Finagle.” Engineering, Twitter, 13 Feb 2014, [URL.][netty-at-twitter-with-finagle]

[<a name="open-sourcing-zuul-2">3</a>] (Gonigberg, Arthur; Cohen, Mikey; Smith, Michael; Varadarajan,Gaya; Vinukonda, Sudheer; Aroskar, Susheel). “[Open Sourcing Zuul 2][open-sourcing-zuul2].” Netflix Technology Blog, [Netflix TechBlog][netflix-techblog], 21 May 2018, [URL][open-sourcing-zuul2].


### Notes
[<a name="netty-at-twitter">a</a>] Twitter's core services are built with [Finagle][netty-in-finagle], which is built ontop of [Netty][netty].<sup>[[2]](#netty-at-twitter-with-finagle)</sup>  

[<a name="netty-at-netflix">b</a>] Zuul 2 handles all the requests that come into Netflix's cloud infrastructure "handling the network protocol, web server, connection management and proxying work."  Netty is "responsible for handling the network protocol, web server, connection management and proxying work".<sup>[[3]](#open-sourcing-zuul-2)</sup>  

[<a name="why-netty-needs-java11">c</a>] The documentation states java8 is needed; however, the `netty5-parent` needs at least java 11.:

```bash
[INFO] --- maven-enforcer-plugin:3.0.0:enforce (enforce-tools) @ netty5-parent ---
[WARNING] Rule 0: org.apache.maven.plugins.enforcer.RequireJavaVersion failed with message:
Detected JDK Version: 1.8.0-77 is not in the allowed range [11.0.0,).
```

[<a name="bash-profile">d</a>] The `.bash_profile` is located in your home directory `/Users/$USER/.bash_profile`.

[<a name="command-line-tools-note">e</a>] `xcrun` is needed by the `netty5-transport-native-unix-common` module.  [You can obtain this by installing Apple Command Line Tools][xcrun-error]:

```bash
[INFO] --- maven-antrun-plugin:1.8:run (build-native-lib) @ netty5-transport-native-unix-common ---
[INFO] Executing tasks

main:
     [exec] xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
```


[<a name="netty-logo">\*</a>][*Netty Logo Copyright © 2022 The Netty project*][Netty]



[netty]: https://netty.io/index.html
[netty-in-finagle]: https://twitter.github.io/finagle/guide/developers/Extending.html#transport-layer
[netty-at-twitter-with-finagle]: https://blog.twitter.com/engineering/en_us/a/2014/netty-at-twitter-with-finagle
[open-sourcing-zuul2]: https://netflixtechblog.com/open-sourcing-zuul-2-82ea476cb2b3
[netflix-techblog]: https://netflixtechblog.medium.com/
[maven]: https://maven.apache.org/
[oracle-jdk]: https://www.oracle.com/java/technologies/downloads/#java11
[git]: https://git-scm.com/
[build-steps]: https://netty.io/wiki/setting-up-development-environment.html
[xcrun-error]: https://apple.stackexchange.com/questions/254380/why-am-i-getting-an-invalid-active-developer-path-when-attempting-to-use-git-a
[build-native-transports]: https://netty.io/wiki/native-transports#building-the-native-transports
[netty-adopters]: https://netty.io/wiki/adopters.html

