include ./CONFIG

DEPENDS=
CROSSARCH=x64
PWD=$(shell pwd)
PACKAGE_DIR?=${PWD}

DOCKCROSS=$(PWD)/../docker/dockcross
R2PLUGDIR=/usr/lib/radare2/$(VERSION)

all: root
	sudo rm -rf control data
	${MAKE} clean
	mkdir -p data
	cp -rf root/* data
	${MAKE} control
	${MAKE} deb

root:
	cd ../.. && $(DOCKCROSS) --image dockcross/linux-$(CROSSARCH) \
	bash -c 'DESTDIR=/work/scripts/debian/root sh dist/debian/build.sh'

purge: clean
	rm -rf root

summary:
	echo $(VERSION)

include deb.mk