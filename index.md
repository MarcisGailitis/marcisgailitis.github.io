 # Review of GCP videos

## [Where should I run my code?](https://www.youtube.com/watch?v=XcHE5V82OxM) 

Serverless, Containers, VMs

### It depends:

1. Cloud Functions, Functions as a service, for event-driven
2. App Engine, Platform as a Service, for web-facing code
3. Kubernetes Engine, Collections of containers, for containerized systems
4. Compute Engine, VMs, for existing systems

### Compute Engine:
VMs or Infrastructure as a Service

* Docker Container directly on Container Optimized OS
* Managed Instance Groups (templates, autoscaling)
* Load Balancer

#### Ideal for:
* lift and shift
* 1:1 container:VM mapping
* Specific OS/kernel required
* Running databases

### Kubernetes Engine:
Managed Kubernetes or Containers as a Service

#### Why Containers?
* Performance
* Stability
* Isolation
* Portability

#### Why Kubernetes?
* For lots of containers
* Manages Containerized applications & underlying cluster
* Manage Applications, not machines

#### What is Kubernetes Engine?
* Hosted or managed Kubernetes
* Manages the cluster (compute nodes, software updates, cluster autoscaling)

#### Ideal for:
* Run App in Multiple env. (dev/test/prod)
* Full advantage of containers
* CI/CD pipeline

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
