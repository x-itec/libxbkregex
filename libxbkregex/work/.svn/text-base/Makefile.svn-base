LIBNAME=libxbkregex
LIBVERSION=1
LIBSUBVERSION=0
LIBSUBSUBVERSION=0

LIBSRC= xbkregex.c
LIBOBJS = xbkregex.o

LIBN=${LIBNAME}-${LIBVERSION}.${LIBSUBVERSION}

all:
	@echo Run make install 

install:

	make libsinstall
	make test
	
test:	test.o
	c++ -o test test.o -lxbkregex1 

test.o:	test.c 
	make libsinstall;
	c++ -S test.c -I/usr/local/include
	c++ -c test.c -I/usr/local/include  

clean:
	-cd src;rm *.o;rm *.s;
	-rm *.o
	-rm *.s
	-rm test

libs:	
	-mkdir lib; 
	cd src; \
	c++ -fPIC -Wall -c ${LIBSRC}; \
        c++ -g -shared -WL,-soname,${LIBNAME}${LIBVERSION}.so.${LIBVERSION} -o ${LIBNAME}${LIBVERSION}.so.${LIBVERSION}.${LIBSUBVERSION}.${LIBSUBSUBVERSION} ${LIBOBJS} -lc; 

	-cd src; cp lib* ../lib/ 

libsinstall: 
	cd lib; \
	cp lib* /usr/local/lib;\
	ln -sf /usr/local/lib/${LIBNAME}${LIBVERSION}.so.${LIBVERSION}.${LIBSUBVERSION}.${LIBSUBSUBVERSION} /usr/lib/${LIBNAME}${LIBVERSION}.so.${LIBVERSION};\
	ln -sf /usr/lib/${LIBNAME}${LIBVERSION}.so.${LIBVERSION} /usr/lib/${LIBNAME}${LIBVERSION}.so	
	ldconfig
	-mkdir /usr/local/include/xbk
	-mkdir /usr/local/include/xbk/xbkregex
	-cp include/*.h /usr/local/include/xbk/xbkregex/


archive:
	make clean
	make libs
	-mkdir ${LIBN}
	-cp -r lib ${LIBN}/
	-cp -r include ${LIBN}/
	-cp test* ${LIBN}/
	-cp Make* ${LIBN}/
	-cp AU* CH* CO* RE* ${LIBN}/
	tar -czvf ${LIBN}.tar.gz  ${LIBN}
	-cp ${LIBN}.tar.gz /usr/ports/distfiles		
	cd ..;make makesum
