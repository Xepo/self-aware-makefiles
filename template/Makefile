.PHONY: default

# BEGIN self-aware-makefiles
AUTODEP=.maketmp/$$@
.maketmp/%: $(MAKEFILE_LIST)
	@mkdir -p .maketmp
	@make -k -B -n $* > $@.tmp
	@bash -c 'if [[ ! -f $@ || "$$(cat $@ | md5sum)" != "$$(cat $@.tmp | md5sum)" ]]; then echo "> Updated recipe for $*"; mv $@.tmp $@; fi'

.SECONDEXPANSION:
# END self-aware-makefiles

# YOUR RULES HERE
# Add ${AUTODEP} to the list of dependencies for any rule you want makefile to consider unclean when the recipe changes
