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

### Ch8 - Metaprogramming

#### Build systems

$ make

#### Semantic versioning

Major.minor.patch
Major = change API in a non-backward-compatible way
Minor = add to API in a backward-compatible way
Patch = new release does not change API

#### CI Systems

Are essentially cloud build system aka. stuff that runs whenever your code changes, like:

* upload a new version of the documentation,
* upload a compiled version somewhere, 
* release the code to PyPI, 
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
* echo Hello | sha1sum
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
