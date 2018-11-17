# self-aware-makefiles
Makefiles should rebuild targets whose recipes have changed, even if the input files haven't.

Here's a Makefile with the basic elements needed to tell it to rebuild targets whose recipes have changed, even if the inputs files haven't changed.  

This seems like it should be built into make, or at least available as an extension or easily googleable, but I couldn't find anything, so I built my own.

# How to use
1. Copy template/Makefile to your project, add your rules to the bottom of that file.  Note that the self-aware-makefiles stanza has to be above your project's rules.  
2. Add ${SELFAWARE} as a dependency to any target to make it automatically rebuild when that target changes.

# Limitations/Things I haven't figured out how to accomplish
- Allow Makefiles to have different names than 'Makefile'
- Should be able to tell Make to add ${SELFAWARE} as a dependency for every rule.  But match-anything rules are too restrictive.
- '$^' becomes useless, since one of the dependencies of every target is now a tmp file that the self-aware process spits out.
- Haven't tried to get this to work if you have multiple directories in a project with multiple makefiles depending on each other
