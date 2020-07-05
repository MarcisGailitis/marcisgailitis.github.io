# Summaries of various videos, focusing on GCP, missing-semester, Python

## GCP

### [Navigating Google Cloud Platform: A Guide for new GCP users](https://www.youtube.com/watch?v=RynMOvYdsCg)

Extra time on computing and storage

#### Computing

* Virtual Machine
* Containers
* Serverless, a marketing term, which just means is you do not worry about hardware and you pay for that you use a.k.a. Platform as a Service.

##### VMs - Compute Engine

* Cloud Launcher prebuilt images for Compute Engine
* You can ssh into the instance via browser

##### Containers – Container Engine or managed Kubernetes

* Container orchestration engine (DNS server, Service Discovery, Logging, Monitoring, Storage )
* Allows running a large number of containers in prof
* Organizing them into workloads (micro services, scheduled jobs, batch jobs)

##### Containers – App Engine

* Docker Images, with custom Docker file
* Autoscaling
* Endpoint

##### Container Registry

* Container storage
* Works with Container Engine, App Engine, Docker

##### Container Builder

* Container Builder as a Service
* Integrates with Container Registry
* Will take your Docker files & application and build an image for you and host in Container Registry

##### Cloud Functions

No app, just simple function (email, when someone uploads a file, you do not want to build a whole application around it, you just want to listen for the event and then start Cloud function)

#### Networking

* Cloud Virtual Network, Hook up a network on your system in your google cloud project
* Cloud Interconnect, Peer directly with google for faster throughput
* VPN
* Firewall
* CDN, activate through load balancers
* DNS
* Load Balancers

#### Storage

* Files
* Databases
* Big Data

##### Files

* Cloud Storage
  * One set of interface
  * Several types (multi-regional (public data), regional (processed data), nearline & coldline (for long term Storage))

##### Databases (application data)

* SQL
  * Cloud SQL
    * Traditional SQL server
    * Vertically scalable
    * Based on VMs
  * Cloud Spanner
    * Database as a Service
    * Horizontally Scalable
    * Be very careful, it can get expensive for a hobbyist
* NoSQL
  * Cloud Datastore
    * Document-Based
    * Indexable
    * Giant
    * Works very well with App Engine
    * accessible from Compute Engine
  * Cloud Bigtable
    * Columnar
    * Low Latency
    * Need scale to be cost-effective, more than 1 TB of data
* BigData
  * BigQuery
    * Pipe in semi-structured data
    * Analyze it quickly
    * Use SQL to do it

#### Other BigData tools

* Pub/Sub
  * Messaging bus
  * Many to many
* Dataflow
  * Managed service for data analysis
  * Apache Beam
* DataProc
  * Managed Spark and Hadoop
  * With Autoscaling

Cloud Pub/Sub and Cloud Storage are at the center hub for GCP process communications.

#### Administration & Reporting

* Stackdriver Logging
Cross-Cloud Logging (GCP, AWS, Azure, etc.)
* Stackdriver Monitoring
Cross-Cloud Monitoring (GCP, AWS, Azure, etc.)
* Stackdriver Trade
  * Automatic
  * Enabled through an SDK
  * Links to logs
* Stackdriver Error Reporting
* Stackdriver Debugging

#### Security

* Cloud IAM
  * Role-based permissions
  * Fine-grained controls

### [Where should I run my code?](https://www.youtube.com/watch?v=XcHE5V82OxM)

Serverless, Containers, VMs

#### It depends

1. Cloud Functions, Functions as a Service, for event-driven
2. App Engine, Platform as a Service, for web-facing code
3. Kubernetes Engine, Collections of containers, for containerized systems
4. Compute Engine, VMs, for existing systems

#### Compute Engine

VMs or Infrastructure as a Service

* Docker Container directly on Container Optimized OS
* Managed Instance Groups (templates, autoscaling)
* Load Balancer

##### Ideal for

* lift and shift
* 1:1 container:VM mapping
* Specific OS/kernel required
* Running databases

#### Kubernetes Engine

Managed Kubernetes or Containers as a Service

##### Why Containers

* Performance
* Stability
* Isolation
* Portability

##### Why Kubernetes

* For lots of containers
* Manages Containerized applications & underlying cluster
* Manage Applications, not machines

##### What is the Kubernetes Engine

* Hosted or Managed Kubernetes
* Manages the cluster (compute nodes, software updates, cluster autoscaling)

##### Kubernetes Engine Ideal for

* Run App in Multiple env. (dev/test/prod)
* Full advantage of containers
* CI/CD pipeline

#### App Engine

Let us run & scale your code
or Platform as a Service

##### What is App Engine

* "Serverless" before it was cool
* Write it this way, we will scale it for you
* Runs Docker containers
* Open Source Runtime: Node.js, Ruby, Java, Python, Go, etc
* Uses Gvisor, Application Kernel for Containers, which allows to run arbitrary code safely

##### App Engine Ideal for

* HTTP/S request-response
* Stateless serving apps
* Scaling to traffic

#### Google Cloud Functions

Event-driven function calls
or Functions as a Service

##### What is Cloud Functions

* A serverless env. to build and connect cloud services
* Event-driven - connect Cloud services via Cloud Pub/Sub, Cloud Storage and HTTP requests
* Serverless:
  * Fully managed execution env.
  * Pay Only for what you use
  * Auto-scales with usage
* Node.js Python 3.7
* Serverless Containers on GCF

##### Good fit

* Serverless
* Using Pub/Sub and/or Cloud Storage
* Don't want to think about runtime env
* Data Transformations (ETL)
* "Glue" for the Cloud

#### Abstraction - what do you want to think about

1. Cloud Functions -  Events, Function Definitions
2. App Engine - Code, HTTP requests
3. Kubernetes Engine - Applications, not computers
4. Compute Engine - Software/OS/disk images

## Review of missing semester

Summaries from lectures: [The Missing Semester of Your CS Education](https://missing.csail.mit.edu/2020/)

### Ch2 - Shell Tools and Scripting

Shell scripting + shell tools for repeatable tasks

#### Scripting

Defining  a variable
`$ foo=bar`

`$ echo $foo`

Spaces in shell are used to separate arguments. Executing foo with 2 arguments, = and bar
`$foo = bar`

Strings with quotes and double quotes

* `$ echo “Value is $foo”` expands variable
* `$ echo ‘Value is $foo’` does not expand variables

##### Simple function

```bash
mcd () {
    mkdir -p “$1”
    cd “$1”
}
```

##### Execute the program

`$ source mcd.sh`
`$ mcd test`

##### $ something

`$0 name` of the program
`$1 - $9` arguments passed to the program
`$#` number of arguments
`$@` expands to all of the arguments
`$$` PID
`$?` - exit code # 0 is good, other numbers not ok
`$_` last argument of the previous program

##### Bang bang

!! executes the last program
`$ apt install some_app`
`$ sudo !!`

##### true/false error codes

`$ true` always exit code 0
`$ false` always exit code 1

##### The output of a command to a variable

`$ foo=$(pwd)`
`$ echo $foo`

`$ “Current directory: $(pwd)”`
`$ echo $(echo $foo)`

##### Wildcards

`$ ls *.sh`
`$ ls project?`
`$ convert image.{jpeg,png}`

#### Useful shell apps

##### shellcheck

to check the bash code scripts

##### tldr

man on steroids

##### find

`$ find . -name scr -type d`
`$ find . -path ‘../test/*.py’ -type f`
`$ find . -mtime -1`
`$ find . -name “*.tmp” -exec rm {}\;`

##### fd

find on steroids

##### locate and updatedb

##### grep -R what where

$ grep foobar mcd.sh
$ grep -R foobar # searches in all files

##### rg (ripgrep)

`$ rg “import requests” -t py ~/scratch`
`$ rg “import requests” -t py -C 5 ~/scratch`
`$ rg -u --files-without-match “^#\!” -t sh`
`$ rg “import requests” -t py -C 5 --stats ~/scratch`

##### up arrow vs. history | grep command_name vs. ctrl+r to search history

fzf bindings vs. history based autosuggestions

##### ls -R vs. tree vs. broot

### Ch3 -  Editors (vim)

#### Modes

* Esc - normal mode = default mode, option to rebind Esc key
* v - visual selection mode (to select lines of text)
* Shift+v - Visual Line mode
* Shift+r - Replace mode
* i - insert mode before the cursor, (as each error is fixed, Esc + h, j, k, l to move to next error)
* : - command line mode

Ctrl + g - shows file info, filename + status + location in file

#### Movement

* Basic movement: h, j, k, l to move around, no arrow buttons, please
* Words: w (next word), e (end of word), b (beginning of word/previous word)
* Lines: 0 (beginning of the line), ^ (first non-blank char), \$ (end of line)
* Screen: H (top of the screen), M (middle of the screen), L (bottom of the screen)
* Scroll:  Ctrl+u (page up, half screen), Ctrl+d (page down, half screen)
* Ctrl+f (page down, full-page) Ctrl+b (page up, full page)
* File: G (last line), gg (first line)
* Line numbers: :number, number + G (moves to a specific line)
* Search: /{regex} (search forwards), n (next), N (previous), ?{regex} (to search backwards),* (on word, searches for next instance)
* Misc: % (Corresponding item)
* Find: f+char (find/to forward/backward {char} on the current line),  F+char (searches backward)

#### Editing

* i (insert), a (append after the cursor), A (appends at the end of the current line),
* o/O (inserts new line below/above cursor and changes mode to insert),
* d{motion} ( delete {motion} e.g. dw deletes the word, d$ is deleting to end of the line, d0 is deleting to the beginning of the line), dd (delete the whole line)
* c{motion} (change {motion}, e.g. cw is change word, like d{motion} followed by i)
* x (delete character (equal do dl)
* y (to copy / “yank”, some other commands like d also copy), p (paste previously deleted text after the cursor)
* r+char replaces char under the cursor
* . (repeats last change),
* u (undo the last command), Ctrl + r (redo the last command), U (undo all commands for the current line)
* J (deletes line break at the end of the line),

#### Counts

* d3w - deletes 3 words
* 2dd - deletes 2 lines
* 6j - moves 6 rows down
* 2w - moves cursor 2 words forward

#### Command-line

* :s/old/new + Enter - substitute old to new only one change
* :s/old/new/g + Enter - substitute old to new all instances on the line
* :%s/old/new/g - substitute all changes in the file
* :#,#s/old/new/g - substitute old to new all instances on the line b/w lines #
* :%s/old/new/gc - all changes in the file + confirmation
* :!command - to execute external command
* :w filename - to write current vim content to a file filename
* :w - to save current vim content
* :r filename - inserts content from a file filename below the cursor line
* :r !ls - to insert content from an external command
* :q - to quit
* :w - to write
* :h - for help, :q to quit help
* :e - to open file
* :q! - quits no save
* :wq - write + quit
* ZZ - write + quit

* `:set ignorecase` or `:set ic` (ignore case)
* `:set incsearch` or `:set is` (partial match)
* `:set hlsearch` or `:set hls` (highlight search)
* `:set noxxx` (to switch off)

### Ch4 - Data wrangling

Data Wrangling  = changing data format1 -> format2

sed = stream editor works with regex

awk = column-based stream processor

Data wrangling examples:

* text file, log file -> statistics out of it
* anything that goes from a to b

`$ ssh server journalctl`  to view the log file

`$ ssh server journalctl | grep ssh` to view only ssh related logs

`$ ssh server journalctl | grep ssh | grep "Disconnected from"` to further reduce log file

`$ ssh server 'journalctl | grep ssh | grep "Disconnected from"' | less` to execute grep commands on the server-side

`$ ssh server 'journalctl | grep ssh | grep "Disconnected from"' > ssh.log` to save grepped log file locally

>Jan 17 03:13:00 thesquareplanet.com sshd[2631]: Disconnected from invalid user Disconnected from 46.97.239.16 port 55920 [preauth]

`$ cat ssh.log | sed 's/.*Disconnected from//'` substitute sed expression, to remove everything including Disconnected from text
> invalid user Disconnected from 46.97.239.16 port 55920 [preauth]

`$ cat ssh.log | sed -E 's/.*Disconnected from (invalid | authenticating )?user (.*) [^ ]+ port [0-9]+( \[preauth\])?$/\2/'` to create and access capture group with user names only

`$cat ssh.log | sed -E 's/.*Disconnected from (invalid |authenticating )?user (.*) [^ ]+ port [0-9]+( \[preauth\])?$/\2/' | sort | uniq -c | sort -nk1,1 | tail -n10` to group and sort most popular usernames

`$ cat ssh.log | sed -E 's/.*Disconnected from (invalid |authenticating )?user (.*) [^ ]+ port [0-9]+( \[preauth\])?$/\2/' | sort | uniq -c | sort -nk1,1 | tail -n10 | awk '{print $2}' | paste -sd` to print only 2nd column and convert column of usernames to to comma separated row

### Ch5 - Command-line environment

#### Job Control

`$ sleep 20` Ctrl+c to terminate sleep program, which sends SIGINT (Signal Interrupt) signal to the kernel.

`$ man signal` to see all available signals, at least 18 of them

* SIGSTOP to stop, SIGCONT to continue
* SIGQUIT to quit
* SIGKILL can not be captured
when you logoff, terminal send Hangup signal to all active applications

`$ sleep 100`
ctrl+z to sent Sigstop,  to suspend

`$ nohup sleep 2000 &`

* nohup encapsulates your command and ignores Hangup signal, so that command keeps running
* & to send the program to background

`$ jobs` to see all active programs and their statuses

`$ bg %1` to run a suspended program

`$ jobs` all programs are running again

`$ kill -STOP %1` #kill allows you to send any UNIX signal, stop in this case, %1=identifier

`$ jobs`

#### Terminal Multiplex

Tmux allows executing “virtual shells”. Huge benefit in remote sessions, as it will not kill the running apps in a remote terminal.

Tmux allows creating different workspaces in the same terminal, Sessions, Windows Panes.

`$ tmux new -s "session name" -n " window name"`
`$ tmux neww -n " window name2"`

##### Sessions

`$ tmux` starts a new session

`$ tmux ls` lists the current sessions

`ctrl-b d` to detach from current tmux session

`$ tmux a` to attach the latest session?

`$ tmux attach -t 0` to attach specific session

`$ tmux new -s foobar` creates a new session named foobar

`$ tmux rename-session -t 0 foobar` to rename existing session
ctrl-b $ # to rename session

##### Windows

`ctrl-b c` to create a new window in session, ctrl+d to terminate the window

`ctrl-b n/p` to move to next/previous window

`ctrl-b 0-9` to switch to a specific window

`ctrl-b w` lists current windows

`ctrl-b ,` to rename current window

##### Panes

`ctrl-b %/”` to split pane vertically, horizontally

`ctrl-b arrow` to switch b/w panes

`ctrl-b z` to zoom in/out from specific pane

`ctrl-b space` to change the layout of pines in the current window

#### Dotfiles

##### Alias

alias alias_name="command_to_alias arg1 arg2"

\$ alias ll=’ls -lah’
\$ alias gs=”git status”
\$ alias sl=ls
\$ alias mv=”mv-i”

Aliases are saved locally and are removed once the terminal is closed. Dotfiles are a solution for that.

\$ vim ~/.bashrc
alias sl=ls

#### ssl

Remote machines
ssh = secure shell
\$ ssh user@address
\$ logout
\$ ssh user@address ls -la # ssh | grep what_to find allows to execute commands remotely and then pipe it locally

To avoid entering the password every time, use ssh-keys.

\$ ssh-keygen -o -a 100 -t ed25519 -f ~/.ssh/id_ed25519
You should choose a passphrase, to avoid someone who gets hold of your private key to access authorized servers.

ssh will look into .ssh/authorized_keys to determine which clients it should let in. To copy a public key over you can use: cat .ssh/id_ed25519.pub | ssh foobar@remote 'cat >> ~/.ssh/authorized_keys'
A simpler solution can be achieved with ssh-copy-id where available:
\$ ssh-copy-id -i .ssh/id_ed25519.pub foobar@remote

##### Copy over ssh

Scp
rsync

##### .ssh/config

Host vm

* User foobar
* HostName 172.16.174.141
* Port 2222
* IdentityFile ~/.ssh/id_ed25519
* LocalForward 9999 localhost:8888

Configs can also take wildcards

Host *.mit.edu

* User foobar

An additional advantage of using the ~/.ssh/config file over aliases is that other programs like scp, rsync, mosh, &c are able to read it as well and convert the settings into the corresponding flags.

### Ch6 -  Version Control (Git)

Git, in general, is good for the history of changes + collaboration, will take a snapshot for all content of the folder. Additionally, will give extra information, like who, when, and why made changes to the code.

Folder = Tree
Files = Blob

type blob = array (byte)

type tree = map (string, tree | blob)

type commit = bunch of stuff:

* parents: array (commits)
* author: string
* message: string
* snapshot: tree

type object = blob | tree | commit
objects = map (string, object) # immutable

def store(o):

* id = sha1(o)
* object(id) = o

def load (id):

* return object(id)

reference = map ()string, string)

Commits are immutable, which means that editing commit will make an entirely new commit. References are mutable, meaning you can update references pointing to specific objects.

references:

* commit name
* master - main branch of development
* HEAD - in which commit you are currently looking at

working directory -> staging area -> snapshot (commit)

object = tree or blob or another object, accessed by sha1 hash.
references = link to commits, which are mutable (can be updated to point to a new commit)

* master point to the latest commit in development
* HEAD point s to commit, that we are currently in

Once we have objects and references, that is all there is to Git repo, the two pieces of data it shares. At a high level, all Git commands are just manipulations of these 2 kinds of data.

\$ git init
\$ cd ./git
\$ git status
\$ git add
\$ git status
\$ git commit
\$ git log --all --decorate ---graph -oneline
\$ git cat-file -p sha1_commit_hash #  to see the content of that hash
\$ git checkout # moves the HEAD pointer & changes files in the home directory

Q What exactly does the hash correspond to?
A This is the hash of commit, the commit contains the hashes of the tree + blob

### Ch7 - Debugging and Profiling

#### printf debugging

#### Logging

* to file instead of STOUT
* Severity levels (NFO, DEBUG, WARN, ERROR + coloring)

#### Debugger

A tool that will wrap around your code and will let you run your code awhile keeping control around it:

* Halt execution
* Step through the program
* Inspect values
* Etc

IDEs are using command line debuggers and presenting them in a fancy way. Debuggers are really powerful!

$ python -m pdb filename:
l = list all the code
s = 1 step
restart = restarts the debugger
c = continue
p = evaluate expression and print its value, pp for pretty print (example p arr,  p j, p locals())
q = quits debugger
b = breakpoint, program will stop
c = continue after break points

#### Profilers

how to optimize the code

* time
* ltrace
* cProfile
* memory-profiler
* strace

#### Visualizers

FlameGraph

#### Resource Monitoring

* htop = for processes running in the system
* dstat = computes real-time resource metrics
* iotop = input/output
* df, du for disk metrics
* free = memory usage
* iftop = network usage

### Ch8 - Metaprogramming

#### Build systems

$ make

#### Semantic versioning

major.minor.patch
major = change API in a non-backward-compatible way
minor = add to API in a backward-compatible way
patch = new release does not change API

#### CI Systems

Are essentially cloud build system aka. stuff that runs whenever your code changes, like:

* upload a new version of the documentation
* upload a compiled version somewhere
* release the code to PyPI
* run your test suite
* Maybe every time someone sends you a pull request on GitHub, you want their code to be style checked and you want some benchmarks to run

As an example of a CI system, the class website is set up using GitHub Pages. Pages is a CI action that runs the Jekyll blog software on every push to master and makes the built site available on a particular GitHub domain. This makes it trivial for us to update the website! We just make our changes locally, commit them with git, and then push. CI takes care of the rest.

#### Testing

Unit test = tests a single feature
Integration Tests = tests interactions b/w different subsystems
Regression Tests = tests things that were broken in past

### Ch9 - Security and Cryptography

#### Entropy

The measure of randomness, Useful for password security.

log base 2 (Nr of possibilities):

* Coin flip = 2 possibilities = log base 2 (2) = 1 bit of entropy
* Dice flip = 6 possibilities = log base 2 (6) = 2.6 bits of entropy
* 4 random words =~ 40 bits of entropy

#### Hash Functions

* maps data of arbitrary size to a fixed size
* sha1 maps arbitrary-sized inputs to 160-bit outputs (which can be represented as 40 hexadecimal characters)
* echo Hello \| sha1sum
* hard-to-invert random-looking (but deterministic) function
* [Lifetimes of cryptographic hash functions](https://valerieaurora.org/hash.html)

#### Applications

* Git, for content-addressed storage
* A short summary of the contents of a file, for software distribution
* Commitment scheme. A commitment scheme is a cryptographic primitive that allows one to commit to a chosen value (or chosen statement) while keeping it hidden to others, with the ability to reveal the committed value later

#### Key derivation functions

* Key derivation functions (KDFs) are used for a number of applications, including producing fixed-length output for use as keys in other cryptographic algorithms.
* Usually, KDFs are deliberately slow, in order to slow down offline brute-force attacks.

#### Symmetric cryptography

* keygen() -> key
* encrypt(plaintext, key) -> ciphertext
* decrypt(ciphertext, key) -> plaintext

Key = randomized, with a really high entropy
The encrypt function has the property that given the output (ciphertext), it’s hard to determine the input (plaintext) without the key

#### Asymmetric cryptography

* keygen() -> (public key, private key)
* encrypt(plaintext: plaintext, public key) -> ciphertext
* decrypt(ciphertext: ciphertext, private key) -> plaintext

### Ch10 Potpourri = miscellaneous

#### Keyboard remapping

In Vim Remap Caps Lock to Ctrl or Esc.

#### Deamons

Systemctl to monitor system.d deamon (to enable, disable, start, stop deamons).
Cron.d to schedule a command.

#### File Systems. Fuse

To have interactivity b/w user space and Kernel.

#### Backups

Are critical! As Hard drive can fail at any moment!

#### API

* curl to fetch content of URL and gives back the response.
* Oauth
* ifthisthenthat

#### Command line arguments

* --help
* --verbose
* interactive mode!
* Recursive mode!
* Double dash, do not interpret arguments as a flags
* rm -i vs. rm -- i

#### Markdown

*word*  = italic

**word** bold

* unordered list item
* unordered list item2

1. ordered list
2. 2nd element in ordered list

`# header`

`## subheading`

[CommonMark](https://commonmark.org/help/)

### Ch11 Q & A

#### What are some tools that you would prioritize learning first

* automate repetitive tasks,
* familiarize with keyboard shortcuts
* text editor
* version control!

#### Python vs. Bash vs. Other

* Bash scripts should be used just for automating running a bunch of commands and that's it!
* Max. 100 lines of code
* no code re-use
* no libraries support.

#### Diff b/w source script.sh and ./script.sh

Both executes the code, but source will execute the script in current bash session, but ./ will start a new bash instance.
You need to source functions to be executed in current bash session!

#### apt install Python3-package-name vs. pip install package-name

Often, apt might be slightly out of date, so use pip, if you care about latest features.

#### Profiling tools

* print stuff using "time"
* Cachegrind

#### Data wrangling tools

* curl
* head
* tail
* Python + Pandas
* Python + Jupyter Notebooks

#### Docker vs. VM

Docker = Container,shares kernel with underlying machine. So underlying kernel needs to be compatible with os in container.

#### Any more Vim tricks

* Vim plugins, undotree
* Leader_key w = :wq, I set leader in many .vimrc files, and I am wondering what does it mean?
* Macros in Vim are nto that hard
* Marks, m + any letter to mark the line, then apostrophe + letter to jump back
* Ctrl+o, to jump to the previous place in file
* :earlier
* Search command is a noun e.g. d/string, will delete till next match of the search pattern
* undodir, for persistent history
