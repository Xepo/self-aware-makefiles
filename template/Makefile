.PHONY: default

# BEGIN self-aware-makefiles
SELFAWARE=.maketmp/$$@
.maketmp/%: $(MAKEFILE_LIST)
	@mkdir -p .maketmp
	@make -k -B -n $* > $@.tmp
	@bash -c 'if [[ ! -f $@ || "$$(cat $@ | md5sum)" != "$$(cat $@.tmp | md5sum)" ]]; then echo "> Updated recipe for $*"; mv $@.tmp $@; fi'

.SECONDEXPANSION:
# END self-aware-makefiles

# YOUR RULES HERE
# Add ${SELFAWARE} to the list of dependencies for any rule that you want Make to consider unclean when the recipe changes
