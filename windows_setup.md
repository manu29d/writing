# Technical Gibberish

### Setting up my Windows system
--------------------------------

I am a sort of an advocate of Linux-based systems but I am not a power user. By any measure. I used Ubuntu based systems for 4 years. MacOS for another 4. And since the past year have fallen in love with Pop!_OS.
Following are the things now are making me switch.

1. Pop!_OS 20.04 raised my average CPU temperatures by about 3-5 degrees Celcius.
2. My favourite extension Maximus 3 no longer works. (Seriously, this feature should just be built in).
3. The cross between i3 and Gnome is a hodge-podge in my opinion and distracting (I know you can turn it off).

You could argue that I have been around linux based systems long enough to know how to fix these non-issues. But I am now 30 years old and I want to get to work before worrying about how to fix my DE to my liking. I'll live with a few compromises if it makes me faster.
Give me things on a silver plate so that I can `git clone` my work related stuff and get to work.

So, I temporarily decided to give Windows a try. (yes, I know what you're thinking). I can downgrade back to 18.04 and live happily ever after. But every hiccup is an opportunity to learn something new and I am going to use this opportunity to learn about development on Windows. Because many of my colleagues are on Windows developing Java based applications. I need to get context.

Don't worry. I am still using Pop!_OS 18.04 on my work laptop. I won't jeopardise my work hours for experimenting with a new OS and to learn a new way of working. This is a weekend exercise.

### Background

I own a ThinkPad X1 Extreme Gen 1 laptop as my personal driver. I want to play the occasional games I have on Steam and hence this one has Windows. The last time I touched Windows for anything other than CS:GO was back in college for running Blender. On Windows 7. I gave up immediately as Windows 8 came out.

So, let's note the changes that came out since then
1. Windows has workspaces now!!!
2. WSL2 is around the corner
3. Windows terminal looks promising
4. winget-cli is coming
5. Choco and scoop are here to manage the rest
6. You have a proper desktop environment and don't boot into the start menu

My weapons of choice that I will be validating this on
1. Vim
2. A tiling terminal emulator (like Tilix or iTerm2)
3. Ease of switchinng context (we'll get to that)

### Let's get started

*Disclaimer*: Let's not forget that I did only surface level research for everything because I wanted to get over it fast.

#### The command line

You have `cmd`, `powershell`, `WSL` (download your distro's binary from the Windows Store, for which you will need a Windows Account). Note that all these are slower to start than the alternative in Linux or Mac.
The satisfaction of just hitting `Ctrl + Alt + T` and firing away commands is not available.

Here are the options I tried:

1. _Cmder - Good for people coming from Linux_

Good alternative to CMD and PowerShell. Was designed for people who miss things as they were in their Linux system or Mac.

You can configure many many things. But you can't set a shortcut to open a certain profile directly in a new pane/tab.

You have 2 options to choose from - lite version without git and the full version. Both of these will be downloaded to a location of your choice and you can then change the PATH variable to point to the executable's folder. I used it for more than 10 days. It was fun and easy to get used to.

However, there's a very slight delay between hitting your key and actually seeing the character on screen. It's every bit as annoying as it sounds.

2. _Windows Terminal - The prodigal son_

Splitting was the thing of note. You can configure it to split to `auto`. Which means, it will decide between splitting horiontally or vertically - based on which will give more area to the new pane. Similar to i3.

Settings are pretty intuitive and easy to configure. There are shortcuts to open a new pane with a new profile (wsl, powershell, cmd). `settings.json` is located somewhere and can be accessed by `Ctrl + ,`. Hit the menu icon with an `Alt + Click` and you will be presented with the `defaults.json`. I just compared my two files side by side and went to the configuration documentation whenever I needed.

3. _Terminus - Fancy looks_

Literally just learned about it while typing this out. Looks promising. Should give it a try. No idea what it does to my RAM or CPU. Will have to check.

*Note*: I discovered `Nerd Fonts` while setting up `oh-my-psh` (there's 2 with the same name, different capitalization). I think it's a pretty smart amulgamation for people looking for developer fonts.
*Note 2*: Everyone uses and recommends `Git bash` that comes with Github for Desktop. Tried it. Didn't suit me. I needed the splitting because I usually switch context between tests and seeing logs. I want it to be on the same screen. YMMV.

#### Vim

Installing `gVim` was the way to go becuase `vim` on a command line on windows is just not usable as soon as you resize your pane. I want to be able to hit one shortcut and fire away commands. Also, installing vim somehow produces 4 executables. `Vim Readonly`, `vim diff`, `gvim` and one other which I can't remember. If I am going to be using vim like this, I want to be able to hit the `Windows` key, type vim and press enter without ever having to look at that part of the screen.

So, a facepalm and time for alternatives. `choco install neovim` and FVim to the rescue. Awesome!

...but it opens up with in the `C:\` drive as cwd. Which makes even `fzf` slow. Hmmm. Fix: Make a `dev` directory and write `cd ~/dev` at the top of your `vimrc`/`_viminfo`.

Rest of it was smooth sailing and I didn't have to learn anything new.

*Note*: Shifted from `pathogen` to `vim-plug` and I think everyone else should too.
*Note 2*: Between `fzf` and `CtrlP`, I use `CtrlP` because of the way it loads the files to search for. It looks for the nearest `.git` folder and then a custom command (`git ls-files`) makes sure I'm only loading files in the cache that I care about.

#### VSCodium

I know this is an argument that I could just use Microsoft's editor's non-snitching cousing with vim mode. And be done with it. But no. And the reason is simple:

Window splitting in vim makes me super productive. You tell me an editor that has window splitting and tab management and navigation as intuitive and memory efficient as vim, I'll switch without blinking. Plus I see 75+ lines of code in a single window. Make sure your editor does that too.
Most of our time as a software developer is gone in looking at function definitions and implementing our classes based on a library we imported. Or designing our class-object structures in a way that having them open side by side gives more clarity and results in more efficiency.
Having things open side by side is a boon to productivity. I would like to keep that.

### Other things of note

#### Window snapping/tiling in Windows

It is intuitive and fun and keeps you guessing. Keep pressing the same shortcut (Win + arrow keys) and the window will ultimately appear in the tile/space/monitor you want.

- There's no way to arrange your workspaces after you've created them.
- You can set a three-finger swipe to navigate between workspaces left and right. Like a Mac.
- Worspaces span across monitors. And you can't drag and drop windows directly from one monitor to the other on a different workspace.
- To move windows across workspaces, go to overview (I setup a three-finger swipe up action for it or you can press `Win + Tab`), and then click and drag them.

#### Choco and Scoop

Scoop promises to be for people who miss apt/homebrew. And I quite liked the way dependencies were managed and file/folder arrangements were made by the software out of the box.

But choco has more support and is the de-facto standard. I had both on my system for some time. Ultimately saw myself using choco more because more packages were available there.

#### Git

This one's puzzling and by far the most irritating part of the whole process. What is the standard way of installing this? Is it via scoop/choco? Is it via git-for-windows? Is it via Github for Windows? Git Kraken?

I tried a few alternatives and ended up with 3-4 binaries for git. All different versions and no one complained about git being already installed. Which means none of thee checked for it. Makes sense for choco and scoop. They look at specific directories. Cmder came with it's own. Github for Windows has other ideas. Kraken and Github each added an ssh key to my aacount that just felt too automatic for my control.

#### PostgreSQL

Use choco to install. Tells you it created a password for you. That password is wrong. Okay, how to change/reset it? Well, you have to login first.

PGAdmin: can you please hurry up.

#### Ruby

What ruby version manager are you guys using? Should I install it with devkit? Without? How to install another version and not have it write over all my `C:\` in the background?

#### IntelliJ/Eclipse/Java

Can I please just get started on my project without having to download the entire internet? And people here were complaining about `node_modules`.

#### Docker

> _You need Windows Home 19018+_

Wait. I'm on Windows Home?

- Windows Home does not support Hyper-V
- Windows 1909 came out in last quarter of 2019. Other versions are "Insider Previews"
- To login to Insider Preview builds, you need a microsoft account
- You need to set "Disgnostics Data" to _Full_ which means max telemtry
- Install preview builds at your own risk, because things might break

### Conslusion

a big **NOPE**

I am now looking at distrowatch. Solus, Zorin, and Mx Linux look promising.
