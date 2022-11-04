<h1>Burp Suite: The Basics Walkthrough</h1>

<h2>Task 1: Introduction: Outline</h2>

Welcome to Burp Suite Basics!

This room will cover the foundations of using the Burp Suite web application framework.
Specifically, we will be looking at:

- What Burp Suite is
- An overview of the available tools in the framework
- Installing Burp Suite for yourself
- Navigating and configuring Burp Suite.

We will also be introducing the core of the Burp Suite framework: the Burp Proxy. This room is primarily designed to provide a foundational knowledge of Burp Suite which can then be built upon further in the other rooms of the Burp module; as such, it will be a lot heavier in theory than subsequent rooms, which take more of a practical approach. You are advised to read the information here and follow along yourself with a copy of the tool if you haven't used Burp Suite before. Experimentation is key: use this information in tandem with playing around with the app for yourself to build a foundation for using the framework, which can then be built upon in later rooms.

Let's begin!
<br />
<br />

<b>Answer the question below:</b>

Deploy the machine attached to the task by pressing the green "Start Machine" button, as well as the AttackBox (using the "Start AttackBox" button at the top of the page) if you are not using your own machine.

Note: If you are not using the AttackBox and want to connect to this machine without the VPN, you can do so using this link once the machine has fully loaded and an IP address is displayed: https://10-10-75-35.p.thmlabs.com.

    No answer needed

<h2>Task 2: Getting Started: What is Burp Suite</h2>

</p>

Put simply: Burp Suite is a framework written in Java that aims to provide a one-stop-shop for web application penetration testing. In many ways, this goal is achieved as Burp is very much the industry standard tool for hands-on web app security assessments. Burp Suite is also very commonly used when assessing mobile applications, as the same features which make it so attractive for web app testing translate almost perfectly into testing the APIs (Application Programming Interfaces) powering most mobile apps.

At the simplest level, Burp can capture and manipulate all of the traffic between an attacker and a webserver: this is the core of the framework. After capturing requests, we can choose to send them to various other parts of the Burp Suite framework -- we will be covering some of these tools in upcoming rooms. This ability to intercept, view, and modify web requests prior to them being sent to the target server (or, in some cases, the responses before they are received by our browser), makes Burp Suite perfect for any kind of manual web app testing.

There are various different editions of Burp Suite available. We will be working with the <b>Burp Suite Community edition</b>, as this is free to use for any (legal) non-commercial use. The Burp Suite Professional and Enterprise editions both require expensive licenses but come with powerful extra features:

- <b>Burp Suite Professional</b> is an unrestricted version of Burp Suite Community. It comes with features such as:
    - An automated vulnerability scanner
    - A fuzzer/bruteforcer that isn't rate limited
    - Saving projects for future use; report generation
    - A built-in API to allow integration with other tools
    - Unrestricted access to add new extensions for greater functionality
    - Access to the Burp Suite Collaborator (effectively providing a unique request catcher self-hosted or running on a Portswigger owned server)
In short, Burp Pro is an extremely powerful tool -- which is why it comes with a £319/$399 price tag per user for a one-year subscription. For this reason, Burp Pro is usually only used by professionals (with licenses often being provided by employers).
- <b>Burp Suite Enterprise</b> is slightly different. Unlike the community and professional editions, Burp Enterprise is used for continuous scanning. It provides an automated scanner that can periodically scan webapps for vulnerabilities in much the same way as software like <b>Nessus</b> performs  automated infrastructure scanning. Unlike the other editions of Burp Suite which allow you to perform manual attacks from your own computer, Enterprise sits on a server and constantly scans target web apps for vulnerabilities.

Due to the prohibitive costs involved with either of these editions of Burp Suite, we will stick to the core feature-set provided by Burp Suite Community.

<b>Note:</b> Burp Suite for Windows is featured in the screenshots for many demonstrations; however, there are no differences between this and the copy of Burp Suite installed on the AttackBox.
<br />
<br />

<b>Answer the question below:</b>
    
<b>Which edition of Burp Suite will we be using in this module?</b>
    
    Burp Suite Community
    
<b>Which edition of Burp Suite runs on a server and provides constant scanning for target web apps?</b>
    
    Burp Suite Enterprise
    
<b>Burp Suite is frequently used when attacking web applications and ______ applications.</b>
    
    Mobile
    
<h2>Task 3: Getting Started: Features of Burp Community</h2>

</p>
    
Whilst Burp Community has a relatively limited feature-set compared to the Professional edition, it still has many superb tools available. These include:   

- <b>Proxy:</b> The most well-known aspect of Burp Suite, the Burp Proxy allows us to intercept and modify requests/responses when interacting with web applications.
- <b>Repeater:</b> The second most well-known Burp feature -- Repeater -- allows us to capture, modify, then resend the same request numerous times. This feature can be absolutely invaluable, especially when we need to craft a payload through trial and error (e.g. in an SQLi -- Structured Query Language Injection) or when testing the functionality of an endpoint for flaws.
- <b>Intruder:</b> Although harshly rate-limited in Burp Community, Intruder allows us to spray an endpoint with requests. This is often used for bruteforce attacks or to fuzz endpoints.
- <b>Decoder:</b> Though less-used than the previously mentioned features, Decoder still provides a valuable service when transforming data -- either in terms of decoding captured information, or encoding a payload prior to sending it to the target. Whilst there are other services available to do the same job, doing this directly within Burp Suite can be very efficient.
- <b>Comparer:</b> As the name suggests, Comparer allows us to compare two pieces of data at either word or byte level. Again, this is not something that is unique to Burp Suite, but being able to send (potentially very large) pieces of data directly into a comparison tool with a single keyboard shortcut can speed things up considerably.
- <b>Sequencer:</b> We usually use Sequencer when assessing the randomness of tokens such as session cookie values or other supposedly random generated data. If the algorithm is not generating secure random values, then this could open up some devastating avenues for attack.

In addition to the myriad of in-built features, the Java codebase also makes it very easy to write extensions to add to the functionality of the Burp framework. These can be written in Java, Python (using the Java Jython interpreter), or Ruby (using the Java JRuby interpreter). The Burp Suite Extender module can quickly and easily load extensions into the framework, as well as providing a marketplace to download third-party modules (referred to as the "BApp Store"). Whilst many of these extensions require a professional license to download and add in, there are still a fair number that can be integrated with Burp Community. For example, we may wish to extend the inbuilt logging functionality of Burp Suite with the Logger++ module.
<br />
<br />

<b>Answer the question below:</b>
    
<b>Which Burp Suite feature allows us to intercept requests between ourselves and the target?</b>
    
    Proxy
    
<b>Which Burp tool would we use if we wanted to bruteforce a login form?</b>
    
    Intruder
    
<h2>Task 4: Getting Started: Installation</h2>

</p>
    
Note: The AttackBox already has Burp Suite installed, so please feel free to skip this task if you do not intend to use Burp Suite locally.

Burp Suite is one of those tools that is very useful to have around, whether you're explicitly assessing a web or mobile application for a pentest/bug bounty, or are simply wanting to debug a new feature in a web app you are developing. For this reason, it is important to know how to install Burp Suite on a variety of platforms, rather than just using it inside a pentesting OS such as Kali or Parrot. You never know when you might need it!

Fortunately, PortSwigger have made installing Burp Suite extremely easy on Linux, macOS, and Windows, providing dedicated installers for all three. As a Java application, Burp can also be downloaded as a JAR archive and run on effectively anything that will support a Java runtime environment.

Burp Suite comes pre-packaged with Kali Linux, so you should not need to install it there. If, for some reason, Burp is missing from your Kali installation, you can easily install it from the Kali apt repositories.

For other systems, we can download installers from https://portswigger.net/burp/releases/professional-community-2022-9-5?requestededition=community&requestedplatform=.

From the dropdown menus, we can select our operating system, as well as whether we want Burp Suite Community or Burp Suite Professional:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199902225-fbe7accc-b6d0-4f26-8015-12c0fab40a7f.png" height="50%" width="50%" alt="Burp"/>
</p>

We can then click the "Download" button to start downloading the Burp Suite installer. No matter which operating system you are using, <b>make sure to use Burp Suite Community Edition</b>.

Once we have verified the integrity of our download, we can install it in the normal way for our operating system (e.g. Running the executable in Windows or executing the script from the terminal with <b>sudo</b> in Linux).

<b>Note:</b> If installing in Linux, you can choose to install either with or without super-user permissions. If you decide not to use <b>sudo</b> when executing the script, Burp Suite will be installed in your home directory at 

    ~/BurpSuiteCommunity/BurpSuiteCommunity 
and will not be added to your <b>PATH</b>.

The installation wizard is very intuitive. It is generally safe to accept the suggested defaults, regardless of your operating system; however, it is still sensible to read through the installer carefully.

With Burp Suite installed, we can now start up the application. The first time we use it, Burp Suite will ask us to read and accept its terms and conditions; make sure you do so before accepting or declining them!

With the terms and conditions accepted, we are presented with another menu. We will go through this in the next task.
<br />
<br />

<b>Answer the question below:</b>

<b>If you have chosen not to use the AttackBox, make sure that you have a copy of Burp Suite installed before proceeding.</b>

    No answer needed
    
<h2>Task 5: Getting Started: The Dashboard</h2>

</p>

When we open Burp Suite and have accepted the terms and conditions, we are met with a window asking us to select the project type.

This window doesn't give us many options in Burp Community. Burp Pro would allow us to save our work to the disk or load a previously saved project at this point. All we can do here is click "Next", however.

The next window allows us to choose a configuration for Burp Suite. Leaving this at the default is perfect for most situations:

Click "Start Burp", and the main Burp Suite interface will open!

The first time you open Burp Suite, you may be presented with a screen of training options. These are well worth reading through if you get the time.

If not (and in any subsequent sessions regardless), you will be presented with the slightly daunting Burp Dashboard:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199903453-ee1cfe67-ec25-4b6b-821b-a81daa20e08c.png" height="50%" width="50%" alt="Burp"/>
</p>

Don't be alarmed if this doesn't make too much sense just yet -- it soon will!

In short, the Dashboard interface is split into four quadrants:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199903453-ee1cfe67-ec25-4b6b-821b-a81daa20e08c.png" height="50%" width="50%" alt="Burp"/>
</p>

1. The Tasks menu allows us to define background tasks that Burp Suite will run whilst we use the application. The Pro version would also allow us to create on-demand scans. The default "Live Passive Crawl" (which automatically logs the pages we visit) will be more than suitable for our uses in this module.
2. The Event log tells us what Burp Suite is doing (e.g. starting the Proxy), as well as information about any connections that we are making through Burp.
3. The Issue Activity section is exclusive to Burp Pro. It won't give us anything using Burp Community, but in Burp Professional it would list all of the vulnerabilities found by the automated scanner. These would be ranked by severity and filterable by how sure Burp is that the component is vulnerable.
4. The Advisory section gives more information about the vulnerabilities found, as well as references and suggested remediations. These could then be exported into a report.
Clicking on one of the example vulnerabilities in the Issue Activity section gives us an idea of what this looks like:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199903797-3d5743b7-cc40-426e-8d86-d403880c3a48.png" height="50%" width="50%" alt="Burp"/>
</p>

Throughout the various tabs and windows of Burp Suite, you will find little help icons: a question mark within a circle.

Clicking on these will open a new window containing help for the section, for example:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199903909-18b6690e-05f9-4482-8a22-20c870776f97.png" height="50%" width="50%" alt="Burp"/>
</p>

These are extremely useful if you're ever stuck and don't know what a feature does, so make good use of them!
<br />
<br />

<b>Answer the question below:</b>

<b>Open Burp Suite and have a look around the dashboard. Make sure that you are comfortable with it before moving on.</b>

    No answer needed
    
<h2>Task 6: Getting Started: Navigation</h2>

</p>

Navigating around the Burp Suite GUI by default is done entirely using the top menu bars:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199904316-e0c1c98f-3867-412d-93bd-61ee8bffbb82.png" height="50%" width="50%" alt="Burp"/>
</p>

These allow you to switch between modules (along the top row of the attached image). If the selected module has more than one sub-tab, then these can be selected using a second menu bar which appears directly below the original bar (the bottom row of the image above). It is common for module-specific settings to be provided in these sub-tabs (as is the case with the Proxy Options above).

Tabs can also be popped out into separate windows should you prefer to view multiple tabs separately. This can be done by clicking "Window" in the application menu at the top of the screen, then choosing to "Detach" tabs:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199904400-be2ea83a-81b1-4f69-a992-eac670152076.png" height="50%" width="50%" alt="Burp"/>
</p>

These can be reattached in the same way.

In addition to the menu bar, Burp Suite also has keyboard shortcuts that allow quick navigation to key tabs. By default, these are:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199904400-be2ea83a-81b1-4f69-a992-eac670152076.png" height="50%" width="50%" alt="Burp"/>
</p>

Shortcut - Does
- Ctrl + Shift + D - Switch to the Dashboard
- Ctrl + Shift + T - Switch to the Target tab
- Ctrl + Shift + P - Switch to the Proxy tab
- Ctrl + Shift + I - Switch to the Intruder tab
- Ctrl + Shift + R - Switch to the Repeater tab

We will look at how we can view and change these in the next task.
<br />
<br />

<b>Answer the question below:</b>

<b>Get comfortable navigating around the top menu bars.</b>

    No answer needed
    
<h2>Task 7: Getting Started: Options</h2>

</p>

Before we start learning about the Burp Proxy, let's take a look at the options available for configuring Burp Suite.

- Global settings can be found in the User options tab along the top menu bar.
- Project-specific settings can be found in the Project options tab.

The options provided in the User options tab will apply every time we open Burp Suite. In contrast, the Project options will only apply to the current project. Given that we can't save projects in Burp Community, this means that our project options will reset every time we close Burp.

There are far too many options to cover them all, so let's just look at the available categories and highlight a few of the more few important settings. We will start with the User Options tab.

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199905265-3b60aa9f-e626-40a4-b80e-9756dd3489d3.png" height="50%" width="50%" alt="Burp"/>
</p>

The settings here apply globally (i.e. they control the Burp Suite application -- not just the project). That said, many of them can be overwritten in the project settings.

There are four main sub-sections of the User options tab:

- The options in the <b>Connections</b> sub-tab allow us to control how Burp makes connections to targets. For example, we can set a proxy for Burp Suite to connect through; this is very useful if we want to use Burp Suite through a network pivot.
- The <b>TLS</b> sub-tab allows us to enable and disable various TLS (Transport Layer Security) options, as well as giving us a place to upload client certificates should a web app require us to use one for connections.
- An essential set of options: <b>Display</b> allows us to change how Burp Suite looks. The options here include things like changing the font and scale, as well as setting the theme for the framework (e.g. dark mode) and configuring various options to do with the rendering engine in Repeater (more on this later!).
- The <b>Misc</b> sub-tab contains a wide variety of settings, including the keybinding table (HotKeys), which allowing us to view and alter the keyboard shortcuts used by Burp Suite. Familiarising yourself with these settings would be advisable, as using the keybinds can speed up your workflow massively.

With these options, we can customise our Burp install to suit our individual preferences.

Let's move on to look at the project-specific configurations available in the Project options tab.

There are five sub-tabs here:

- <b>Connections</b> holds many of the same options as the equivalent section of the User options tab: these can be used to override the application-wide settings. For example, it is possible to set a proxy for just the project, overriding any proxy settings that you set in the User options tab. There are a few differences between this sub-tab and that of the User options, however. For example, the "Hostname Resolution" option (allowing you to map domains to IPs directly within Burp Suite) can be very handy -- as can the "Out-of-Scope Requests" settings, which enable  us to determine whether Burp will send requests to anything you aren't explicitly targeting (more on this later!).
- The <b>HTTP</b> sub-tab defines how Burp handles various aspects of the HTTP protocol: for example, whether it follows redirects or how to handle unusual response codes.
- <b>TLS</b> allows us to override application-wide TLS options, as well as showing us a list of public server certificates for sites that we have visited.
- The <b>Sessions</b> tab provides us with options for handling sessions. It allows us to define how Burp obtains, saves, and uses session cookies that it receives from target sites. It also allows us to define macros which we can use to automate things such as logging into web applications (giving us an instant authenticated session, assuming we have valid credentials).
- There are fewer options in the <b>Misc</b> sub-tab than in the equivalent tab for the "User options" section. Many of the options here are also only available if you have access to Burp Pro (such as those configuring Collaborator). That said, there are a couple of options related to logging and the embedded browser (which we will look at in a couple of tasks) that are well worth perusing.
<br />
<br />

<b>Answer the question below:</b>

<b>Change the Burp Suite theme to dark mode</b>

    No answer needed
    
<b>In which Project options sub-tab can you find reference to a "Cookie jar"?</b>

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199907003-afeb373d-61b1-409d-b2b8-1689c4e0726d.png" height="50%" width="50%" alt="Burp"/>
</p>

    Sessions
    
<b>In which User options sub-tab can you change the Burp Suite update behaviour?</b>

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199907688-4e6f5c52-0f32-4c91-997a-346b2832b938.png" height="50%" width="50%" alt="Burp"/>
</p>

    Misc
    
<b>What is the name of the section within the User options "Misc" sub-tab which allows you to change the Burp Suite keybindings?</b>

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199908241-fd2032e5-8800-463c-8eb5-d2ce580355e2.png" height="50%" width="50%" alt="Burp"/>
</p>

    Hotkeys
    
<b>If we have uploaded Client-Side TLS certificates in the User options tab, can we override these on a per-project basis (Aye/Nay)?</b>

    Aye
    
<b>There are many more configuration options available. Take the time to read through them.

In the next section, we will cover the Burp Proxy -- a much more hands-on aspect of the room.</b>

    No answer needed
    
<h2>Task 8: Proxy: Introduction to the Burp Proxy</h2>

</p>

The Burp Proxy is the most fundamental (and most important!) of the tools available in Burp Suite. It allows us to capture requests and responses between ourselves and our target. These can then be manipulated or sent to other tools for further processing before being allowed to continue to their destination.

For example, if we make a request to https://tryhackme.com through the Burp Proxy, our request will be captured and won't be allowed to continue to the TryHackMe servers until we explicitly allow it through. We can choose to do the same with the response from the server, although this isn't active by default. This ability to intercept requests ultimately means that we can take complete control over our web traffic -- an invaluable ability when it comes to testing web applications.

There are a few configurations we need to make before we can use the proxy, but let's start by looking at the interface.

<b>Note:</b> You do not need to follow along with this task -- just read the information and understand what the Proxy is used for.

When we first open the Proxy tab, Burp gives us a bunch of useful information and background reading. This information is well worth reading through; however, the real magic happens after we capture a request:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199912608-c1fc1cbc-a43c-4e54-865d-5d9c4e4f16e9.png" height="50%" width="50%" alt="Burp"/>
</p>

With the proxy active, a request was made to the TryHackMe website. At this point, the browser making the request will hang, and the request will appear in the Proxy tab giving us the view shown in the screenshot above. We can then choose to forward or drop the request (potentially after editing it). We can also do various other things here, such as sending the request to one of the other Burp modules, copying it as a cURL command, saving it to a file, and many others.

When we have finished working with the Proxy, we can click the "Intercept is on" button to disable the Intercept, which will allow requests to pass through the proxy without being stopped.

Burp Suite will still (by default) be logging requests made through the proxy when the intercept is off. This can be very useful for going back and analysing prior requests, even if we didn't specifically capture them when they were made.

Burp will also capture and log WebSocket communication, which, again, can be exceedingly helpful when analysing a web app.

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199912938-73057280-b8d6-4b60-933b-67481b2b9275.png" height="50%" width="50%" alt="Burp"/>
</p>

It is worth noting that any requests captured here can be sent to other tools in the framework by right-clicking them and choosing "Send to...". For example, we could take a previous HTTP request that has already been proxied to the target and send it to <b>Repeater</b>.

Finally, there are also Proxy specific options, which we can view in the "Options" sub-tab.

These options give us a lot of control over how the proxy operates, so it is an excellent idea to familiarise yourself with these.

For example, the proxy will not intercept server responses by default unless we explicitly ask it to on a per-request basis. We can override the default setting by selecting the "Intercept responses based on the following rules" checkbox and picking one or more rules. The "<b>Or Request Was Intercepted</b>" rule is good for catching responses to all requests that were intercepted by the proxy:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199913805-643ba470-96a7-4a56-a5e5-f6b94f6ead1b.png" height="50%" width="50%" alt="Burp"/>
</p>

The "<b>And URL Is in target scope</b>" is another very good default rule; we will look at scoping later in this room.

You can make your own rules for most of the Proxy options, so this is one section where looking around and experimenting will serve you very well indeed!

Another particularly useful section of this sub-tab is the "Match and Replace" section; this allows you to perform regexes on incoming and outgoing requests. For example, you can automatically change your user agent to emulate a different web browser in outgoing requests or remove all cookies being set in incoming requests. Again, you are free to make your own rules here.
<br />
<br />

<b>Answer the question below:</b>

<b>Which button would we choose to send an intercepted request to the target in Burp Proxy?</b>

    Forward
    
<b>[Research] What is the default keybind for this?

Note: Assume you are using Windows or Linux (i.e. swap Cmd for Ctrl).

Hint: Use what you learnt in a previous task to look up the keybindings used in Burp Suite, then find a keybinding related to forwarding intercepted proxy messages.</b>

    Ctrl+F
    
<h2>Task 9: Proxy: Connecting through the Proxy (FoxyProxy)</h2>

</p>

You've seen the theory; now it's time to start using the proxy for yourself.

There are two ways to proxy our traffic through Burp Suite.

1. We could use the embedded browser (we will cover this in a later task).
2. We can configure our local web browser to proxy our traffic through Burp; this is more common and so will be the focus of this task.

The Burp Proxy works by opening a web interface on 127.0.0.1:8080 (by default). As implied by the fact that this is a "proxy", we need to redirect all of our browser traffic through this port before we can start intercepting it with Burp. We can do this by altering our browser settings or, more commonly, by using a Firefox browser extension called FoxyProxy. FoxyProxy allows us to save proxy profiles, meaning we can quickly and easily switch to our "Burp Suite" profile in a matter of clicks, then disable the proxy just as easily.

<b>Note:</b> All instructions will be given with Firefox in mind, as this is the default browser for both Kali Linux and the TryHackMe AttackBox. If you are using another browser locally then you are advised to use the AttackBox, or you may otherwise need to find alternative methods to those presented in this task. If you can't get the proxy working in your local browser and do not want to use the AttackBox, then you may wish to skip ahead to the Burp Suite Browser task.

There are two versions of FoxyProxy: Basic and Standard. Both versions allow you to change your proxy settings on the fly; however, FoxyProxy Standard gives you a lot more control over what traffic gets sent through the proxy. For example, it will allow you to set pattern matching rules to determine whether a request should be proxied or not: this is more complicated than the simple proxy offered by FoxyProxy basic.

The basic edition is more than adequate for our usage. It is pre-installed and configured in the Firefox browser of the AttackBox, so if you are using the AttackBox, please feel free to skip ahead to the last section of this task.

If you are using your own machine, you can download FoxyProxy Basic here https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-basic/ 

Once installed, a button should appear at the top right of the screen which allows you to access your proxy configurations:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199915027-ef00f4f2-4936-4844-b566-cf3c0830f1b6.png" height="50%" width="50%" alt="Burp"/>
</p>

There are no default configurations, so let's click on the "Options" button to create our Burp Proxy config.

This will open a new browser tab with the FoxyProxy options page:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199915149-981028bf-990a-4062-acf0-ea829edac2a5.png" height="50%" width="50%" alt="Burp"/>
</p>

Click on the "Add" button and fill in the following values:

Title: Burp (or anything else you prefer)
Proxy IP: 127.0.0.1
Port: 8080

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199915875-41d4f528-6ac0-47df-b257-2c77df1aa326.png" height="50%" width="50%" alt="Burp"/>
</p>

Now click "Save".

When you click on the FoxyProxy icon at the top of the screen, you will see that that there is a configuration available for Burp:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199915974-558bbe69-440e-4ffb-9c93-4a8f79f30422.png" height="50%" width="50%" alt="Burp"/>
</p>

If we click on the "Burp" config, our browser will start directing all of our traffic through 127.0.0.1:8080. Be warned: if Burp Suite is not running, your browser will not be able to make any requests when this config is activated!

Activate this config now -- the icon in the menu should change to indicate that we have a proxy running:

Next, switch over to Burp Suite and make sure the Intercept is On:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199916166-75d6fd26-0de1-425a-950d-fdaa6ee835df.png" height="50%" width="50%" alt="Burp"/>
</p>

Now, try accessing the homepage for http://10.10.75.35/ in Firefox. Your browser should hang, and your proxy will populate with the request headers.

Congratulations, you just intercepted your first request!

From here, you can choose to forward or drop the request. Alternatively, you could send it to another tool or perform any number of other actions by right-clicking on the request and selecting an option from the right-click menu.

Remember: Whilst you are connected to the proxy and have the Proxy Intercept switched on, your browser will hang whenever you make a request. A very common mistake when you are learning to use Burp Suite (and indeed, later on!) is to accidentally leave the intercept switched on and ergo be unable to make any web requests through your browser. If your browser is hanging and you don't know why: check your proxy!
<br />
<br />

<b>Answer the question below:</b>

<b>Read through the options in the right-click menu.

There is one particularly useful option that allows you to intercept and modify the response to your request.

What is this option?

Note: The option is in a dropdown sub-menu.</b>

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199917207-5ec82865-dca2-4e75-8289-1925003bd571.png" height="50%" width="50%" alt="Burp"/>
</p>

    Response to this request
    
<b>[Bonus Question -- Optional] Try installing FoxyProxy standard and have a look at the pattern matching features.</b>

    No answer needed
    
<h2>Task 10: Proxy: Proxying HTTPS</h2>

</p>

Note: The AttackBox is already configured to solve the problem posed in this task. If you are using the AttackBox and don't wish to read through the information here, you can skip to the next task.

Great, so we can intercept HTTP traffic -- what's next?

Unfortunately, there's a problem. What happens if we navigate to a site with TLS enabled? For example,

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199917626-91481398-104b-4cb8-91bb-0b24030a057a.png" height="50%" width="50%" alt="Burp"/>
</p>

We get an error.

Specifically, Firefox is telling us that the Portswigger Certificate Authority (CA) isn't authorised to secure the connection.

Fortunately, Burp offers us an easy way around this. We need to get Firefox to trust connections secured by Portswigger certs, so we will manually add the CA certificate to our list of trusted certificate authorities.

First, with the proxy activated head to http://burp/cert; this will download a file called <b>cacert.der</b> -- save it somewhere on your machine.

Next, type about:preferences into your Firefox search bar and press enter; this takes us to the FireFox settings page. Search the page for "certificates" and we find the option to "View Certificates":

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199917847-a5751021-6f14-4f65-ad5e-427c4778ae9f.png" height="50%" width="50%" alt="Burp"/>
</p>

Clicking the "View Certificates" button allows us to see all of our trusted CA certificates. We can register a new certificate for Portswigger by pressing "Import" and selecting the file that we just downloaded.

In the menu that pops up, select "Trust this CA to identify websites", then click Ok:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199917969-c33f495a-4321-4c7d-a2ae-5e78c916baab.png" height="50%" width="50%" alt="Burp"/>
</p>

We should now be free to visit any TLS enabled sites that we wish!
<br />
<br />

<b>Answer the question below:</b>

<b>If you are not using the AttackBox, configure Firefox (or your browser of choice) to accept the Portswigger CA certificate for TLS communication through the Burp Proxy.</b>

    No answer needed
    
<h2>Task 11: Proxy: Proxying HTTPS</h2>

</p>

If the last few tasks seemed overly complex, rest assured, this topic will be a lot simpler.

In addition to giving us the option to modify our regular web browser to work with the proxy, Burp Suite also includes a built-in Chromium browser that is pre-configured to use the proxy without any of the modifications we just had to do.

Whilst this may seem ideal, it is not as commonly used as the process detailed in the previous few tasks. People tend to stick with their own browser as it gives them a lot more customisability; however, both are perfectly valid choices.

We can start the Burp Browser with the "Open Browser" button in the proxy tab:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199918771-6e756cc3-a025-4512-b0bb-1a3ca075ff64.png" height="50%" width="50%" alt="Burp"/>
</p>

A Chromium window will now pop up. Any requests we make in this will go through the proxy.

<b>Note:</b> There are many settings to do with the Burp Browser in the Project options and User options tabs -- make sure to go look at them!

If we are running on Linux as the root user (as we are with the AttackBox), Burp Suite is unable to create a sandbox environment to start the Burp Browser in, causing it to throw an error and die:

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199918908-7c429f35-dbdb-4572-adb1-ecaf27e29279.png" height="50%" width="50%" alt="Burp"/>
</p>

There are two simple solutions to this:

- <b>The smart option:</b> We could create a new user and run Burp Suite under a low privilege account.
- <b>The easy option:</b> We could go to <b>Project options -> Misc -> Embedded Browser</b> and check the <b?Allow the embedded browser to run without a sandbox option</b>. Checking this option will allow the browser to start, but be aware that it is disabled by default for security reasons: if we get compromised using the browser, then an attacker will have access to our entire machine. On the training environment of the AttackBox this is unlikely (and isn't a huge issue even if it does happen), but keep it in mind if you try this on a local installation of Burp Suite.

Be aware that you will need to do this if using the embedded browser on the AttackBox.
<br />
<br />

<b>Answer the question below:</b>

<b>Using the in-built browser, make a request to http://10.10.75.35/ and capture it in the proxy.</b>

<p align="center">
<img src="https://user-images.githubusercontent.com/110497344/199919854-e3938600-69dd-4521-8151-faa60183781d.png" height="50%" width="50%" alt="Burp"/>
</p>

    No answer needed
    
<h2>Task 12: Proxy: Scoping and Targeting</h2>

</p>


