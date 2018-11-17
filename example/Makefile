.PHONY: default

# BEGIN self-aware-makefiles
AUTODEP=.maketmp/$$@
.maketmp/%: $(MAKEFILE_LIST)
	@mkdir -p .maketmp
	@make -k -B -n $* > $@.tmp
	@bash -c 'if [[ ! -f $@ || "$$(cat $@ | md5sum)" != "$$(cat $@.tmp | md5sum)" ]]; then echo "> Updated recipe for $*"; mv $@.tmp $@; fi'

.SECONDEXPANSION:
# END self-aware-makefiles

default: step5.tmp 

step5.tmp: step4.tmp ${AUTODEP}
	uniq -c $< > $@

step4.tmp: step3.tmp ${AUTODEP}
	sort $< > $@

step3.tmp: step1.tmp step2.tmp ${AUTODEP}
	rev step1.tmp step2.tmp > $@

step2.tmp: step1.tmp ${AUTODEP}
	tac $< > $@

step1.tmp: input.txt ${AUTODEP}
	cp $< $@

