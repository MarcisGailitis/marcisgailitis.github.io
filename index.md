# Review of GCP videos

## [Navigating Google Cloud Platform: A Guide for new GCP users](https://www.youtube.com/watch?v=RynMOvYdsCg)

Extra time on computing and storage.

### Computing:
-	Virtual Machine
-	Containers
-	Serverless, a marketing term, which just means is you do not worry about hardware and you pay for that you use a.k.a. Platform as a Service.

#### VMs - Compute Engine:
- Cloud Launcher prebuilt images for Compute Engine
- You can ssh into the instance via browser

#### Containers – Container Engine or managed Kubernetes:
-	Container orchestration engine (DNS server, Service Discovery, Logging, Monitoring, Storage )
-	Allows running a large number of containers in prof
-	Organizing them into workloads (microservices, scheduled jobs, batch jobs)

#### Containers – App Engine:
-	Docker Images, with custom Docker file
-	Autoscaling
-	Endpoint

#### Container Registry:
-	Container storage
-	Works with Container Engine, App Engine, Docker

#### Container Builder:
-	Container Builder as a Service
-	Integrates with Container Registry
-	Will take your Docker files & application and build an image for you and host in Container Registry

#### Cloud Functions:
-	No app, just function (email, when someone uploads a file, you do not want to build a whole application around it, you just want to listen for the event and then start Cloud function)

### Networking:
-	Cloud Virtual Network, Hook up a network on your system in your google cloud project
-	Cloud Interconnect, Peer directly with google for faster throughput
-	VPN
-	Firewall
-	CDN, activate through load balancers
-	DNS
-	Load Balancers

### Storage:
-	Files
-	Databases
-	Big Data

#### Files:
-	Cloud Storage
   -	One set of interface
   -	Several types (multi-regional (public data), regional (processed data), nearline & cold line (Long Term Storage))

#### Databases (application data):
-	SQL
    -	Cloud SQL
        -	Traditional SQL server
        -	Vertically scalable
        -	Based on VMs
    -	Cloud Spanner
        -	Database as a Service
        -	Horizontally Scalable
        -	Be very careful, it can get expensive for a hobbyist
-	NoSQL
    -	Cloud Datastore
        -	Document-Based
        -	Indexable
        -	Giant
        -	Works very well with App Engine 
        -	accesable from Compute Engine
    -	Cloud Bigtable
        -	Columnar
        -	Low Latency
        -	Need scale to be cost-effective, more than 1 TB of data
-	BigData
    -	BigQuery
        -	Pipe in semi-structured data
        -	Analyze it quickly
        -	Use SQL to do it

### Other BigData tools:
-	Pub/Sub
    -	Messaging bus
    -	Many to many
-	Dataflow
    -	Managed service for data analysis
    -	Apache Beam
-	DataProc
    -	Managed Spark and Hadoop
    -	With Autoscaling

Cloud Pub/Sub and Cloud Storage are at the center hub for GCP process communications.

### Administration & Reporting:
-	Stackdriver Logging
    -	Cross-Cloud Logging (GCP, AWS, Azure, etc.)
-	Stackdriver Monitoring
    -	Cross-Cloud Monitoring (GCP, AWS, Azure, etc.)
-	Stackdriver Trade
    -	Automatic
    -	Enabled through an SDK
    -	Links to logs
-	Stackdriver Error Reporting
-	Stackdriver Debugging

### Security:
-	Cloud IAM
    -	Role-based permissions
    -	Fine graned controls


## [Where should I run my code?](https://www.youtube.com/watch?v=XcHE5V82OxM) 

Serverless, Containers, VMs

### It depends:

1. Cloud Functions, Functions as a Service, for event-driven
2. App Engine, Platform as a Service, for web-facing code
3. Kubernetes Engine, Collections of containers, for containerized systems
4. Compute Engine, VMs, for existing systems

### Compute Engine:
VMs 
or Infrastructure as a Service

* Docker Container directly on Container Optimized OS
* Managed Instance Groups (templates, autoscaling)
* Load Balancer

#### Ideal for:
* lift and shift
* 1:1 container:VM mapping
* Specific OS/kernel required
* Running databases

### Kubernetes Engine:
Managed Kubernetes 
or Containers as a Service

#### Why Containers?
* Performance
* Stability
* Isolation
* Portability

#### Why Kubernetes?
* For lots of containers
* Manages Containerized applications & underlying cluster
* Manage Applications, not machines

#### What is the Kubernetes Engine?
* Hosted or Managed Kubernetes
* Manages the cluster (compute nodes, software updates, cluster autoscaling)

#### Ideal for:
* Run App in Multiple env. (dev/test/prod)
* Full advantage of containers
* CI/CD pipeline

### App Engine:
Let us run & scale your code
or Platform as a Service

#### What is App Engine?
* "Serverless" before it was cool
* Write it this way, we will scale it for you
* Runs Docker containers
* Open Source Runtime: Node.js, Ruby, Java, Python, Go, etc
* Uses Gvisor, Application Kernel for Containers, which allows to run arbitrary code safely

#### Ideal for:
* HTTP/S request-response
* Stateless serving apps
* Scaling to traffic

### Cloud Functions:
Event-driven function calls
or Functions as a Service

#### What is Cloud Functions?
* A serverless env. to build and connect cloud services
* Event-driven - connect Cloud services via Cloud Pub/Sub, Cloud Storage and HTTP requests
* Serverless:
    * Fully managed execution env.
    * Pay Only for what you use
    * Auto-scales with usage
* Node.js Python 3.7
* Serverless Containers on GCF

#### Good fit?
* Serverless
* Using Pub/Sub and/or Cloud Storage
* Don't want to think about runtime env
* Data Transformations (ETL)
* "Glue" for the Cloud

### Abstraction - what do you want to think about
1. Cloud Functions, Events, Function Definitions
2. App Engine, Code, HTTP requests
3. Kubernetes Engine, Applications, not computers
4. Compute Engine, Software/OS/disk images

# Review of missing semester
Conspect from lectures: [The Missing Semester of Your CS Education](https://missing.csail.mit.edu/2020/)
## 10) Potpourri = miscellaneous

**1) Keyboard remapping**

In Vim Remap Caps Lock to Ctrl or Escape.

**2) Deamons**

Systemctl to monitor system.d deamon (to enable, disable, start, stop deamons).
Cron.d to schedule a command.

**3) File Systems. Fuse**

To have interactivity b/w user space and Kernel.

**4) Backups**

Are critical! As Hard drive can fail at any moment!

**5) API**

curl to fetch content of URL and gives back the response.
Oauth
ifthisthenthat

**6) Command line arguments**

--help
--verbose
interactive mode!
Recursive mode!
Double dash, do not interpret argumens as a flags
rm -i vs rm -- i

**7) Win manager**

**8) VPN (Virtual Private Network)**

**9) Markdown**

*word* italic
**word** bold

-list item
1 numbered list
# header
##subheading

https://commonmark.org/help/

## 11) Q & A

**What are some tools that you would prioritize learning first?**
* automate repetitive tasks,
* familiarize with keyboard shortcuts
* text editor 
* version control!

**Python vs. Bash vs. Other**

* Bash scripts should be used just for automating running a bunch of commands 
and that's it! 
* Max. 100 lines of code
* no code re-use, 
* no libraries support.

**Diff b/w source script.sh and ./script.sh?**

Both executes the code, but source will execute the script in current bash
session, but ./will start a new bash instance.
You need to source functions to be executed in current bash session!

**apt install Python3-package-name vs. pip install package-name?**

Often, apt might be slightly out of date, so use pip, if you care for latest 
features.

**Profiling tools**

* print stuff using "time", 
* "Cachegrind".

**Data wrangling tools**

* curl
* head
* tail
* Python + Pandas
* Python + Jupyter Notebooks

**Docker vs. VM**

Docker = Container,shares kernel with underlying machine. 
So underlying kernel needs to be compatible with os in container.

**Any more Vim tricks?**
* Vim plugins, undotree
* <Leader>w = :wq, I set <leader> in many .vimrc files, and I am wondering 
what does it mean?
* Macros in Vim are nto that hard
* Marks, m + any letter to mark the line, then apostrophe + letter to jump 
back
* Ctrl+o, to jump to the previous place in file
* :earlier
* Search command is a noun e.g. d/string, will delete till next match of 
the searchpattern
* undodir, for persistent history
