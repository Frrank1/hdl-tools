PREFIX ?= $(abspath ../opt)

.PHONY: all clean mrproper

all: $(PREFIX)/bin/verilator

intall:
$(PREFIX)/bin/verilator: | repo/.git
	@echo "[INFO] Building Verilator"
	@echo "[INFO] Verilator uses a lot of memory to build, limiting jobs to 2"
	(cd repo && \
	autoconf && \
	./configure --prefix=$(PREFIX) && \
	make -j2 && \
	make install) 2>&1 | tee build.log

repo/.git:
	git submodule update --init repo

clean:
	@(cd repo && make clean) >> build.log

mrproper:
	rm -rf repo && git checkout repo
