# marcisgailitis.github.io
      
# Review of GCP videos

# Review of missing semester

## 11) Q and A
### Q) What are some tools that you would prioritize learning first?

A)
* automate repetitive, automated tasks,
* familiarize with keyboard shortcuts
* text editor & version control!

### Q) Python vs. Bash vs. Other
A) Bash scripts are automating running a bunch of commands and that's it!,
max 100 lines, no code re-use, no libraries

Q) diff b/w source script.sh and ./script.sh?
A) Both executes the code, but source will execute the script in current bash
session, but ./will start a new bash instance.
You need to source functions to be executed in current bash session!

Q) apt install Python3-package_name vs pip install package_name?
A) Often times, apt might be slightly out of date, so use pip, if you care for latest features.

Q) Profiling tools
A) print stuff using "time", "Cachegrind",

Q) Data wrangling tools
A) curl, head, tail, Python+Pandas, Pyton + Jupyter Notebooks

Q) Docker vs. VM
A) Docker = Container, shares kernel, with underlying machine. So underlying kernel needs to be competable

Q) Any more Vim tricks?
A)
* Vim plugins, undotree
* <Leader>w = :wq, I see <leader> in many .vimrc files, and I am wondering what does it mean?
* Macros!
* marks, m + any letter to mark the line, then appostorfie + letter to jump back
* Ctrl+o, to jump to the previous place in file
* :earlier
* seach command is a noun e.g. d/string, will delete till next mach of the pattern
* undodir, for persistent history
