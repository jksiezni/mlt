CFLAGS += -I../..

LDFLAGS += -L../../framework -lmlt -lm

include ../../../config.mak

TARGET = ../libmltrotoscoping$(LIBSUF)

OBJS = factory.o \
	   filter_rotoscoping.o \
	   cJSON.o


LDFLAGS += -lm

SRCS := $(OBJS:.o=.c)

all: 	$(TARGET)

$(TARGET): $(OBJS)
		$(CC) $(SHFLAGS) -o $@ $(OBJS) $(LDFLAGS)

depend:	$(SRCS)
		$(CC) -MM $(CFLAGS) $^ 1>.depend

distclean:	clean
		rm -f .depend

clean:	
		rm -f $(OBJS) $(TARGET)

install: all
	install -m 755 $(TARGET) "$(DESTDIR)$(moduledir)"
	install -d $(DESTDIR)$(mltdatadir)/rotoscoping
	install -m 644 filter_rotoscoping.yml "$(DESTDIR)$(mltdatadir)/rotoscoping"

ifneq ($(wildcard .depend),)
include .depend
endif
