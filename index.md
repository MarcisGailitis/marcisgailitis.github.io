# marcisgailitis.github.io
      
# Review of GCP videos

# Review of missing semester

## 11) Q & A
**What are some tools that you would prioritize learning first?**
* automate repetitive tasks,
* familiarize with keyboard shortcuts
* text editor & version control!

**Python vs. Bash vs. Other**
Bash scripts are automating running a bunch of commands and that's it!
Max. 100 lines, no code re-use, no libraries support.

**Diff b/w source script.sh and ./script.sh?**
Both executes the code, but source will execute the script in current bash
session, but ./will start a new bash instance.
You need to source functions to be executed in current bash session!

**apt install Python3-package-name vs pip install package-name?**
Often times, apt might be slightly out of date, so use pip, 
if you care for latest features.

**Profiling tools**
print stuff using "time", "Cachegrind".

**Data wrangling tools**
curl, head, tail, Python+Pandas, Python + Jupyter Notebooks

**Docker vs. VM**
Docker = Container, shares kernel, with underlying machine. 
So underlying kernel needs to be compatible

**Any more Vim tricks?**
* Vim plugins, undotree
* <Leader>w = :wq, I set <leader> in many .vimrc files, and I am wondering what does it mean?
* Macros!
* Marks, m + any letter to mark the line, then apostrophe + letter to jump back
* Ctrl+o, to jump to the previous place in file
* :earlier
* search command is a noun e.g. d/string, will delete till next mach of the pattern
* undodir, for persistent history
