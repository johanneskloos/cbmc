default: tests.log

include ../../src/config.inc
include ../../src/common

ifeq ($(BUILD_ENV_),MSVC)
	exe=../../../src/goto-cc/goto-cl
	is_windows=true
else
	exe=../../../src/goto-cc/goto-cc
	is_windows=false
endif

test:
	@../test.pl -p -c '../chain.sh $(exe) ../../../src/goto-instrument/goto-instrument $(is_windows)'

tests.log:
	@../test.pl -p -c '../chain.sh $(exe) ../../../src/goto-instrument/goto-instrument $(is_windows)'

show:
	@for dir in *; do \
		if [ -d "$$dir" ]; then \
			vim -o "$$dir/*.c" "$$dir/*.out"; \
		fi; \
	done;

clean:
	@for dir in *; do \
		rm -f tests.log; \
		if [ -d "$$dir" ]; then \
			cd "$$dir"; \
			rm -f *.out *.gb; \
			cd ..; \
		fi \
	done
