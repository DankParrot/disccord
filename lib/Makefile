.PHONY: all clean install uninstall

# C compiler
CC=gcc
AR=ar
# Compiler flags
FLAGS=-std=gnu11 -I. -I../include -lpthread -lcjson -lwebsockets -lssl -lcrypto -lcurl
CFLAGS=-fPIC -Wpedantic -Wall -Wextra -march=native
LDFLAGS=-shared
ARFLAGS=-rv

SOURCES=websocket.c client.c discord.c client_internal.c client_api.c websocket_internal.c snowflake.c discord_objects.c
OBJECTS=$(SOURCES:.c=.o)
TARGET=libdisccord.so

INSTALL=/usr/local/lib/

.c.o:
	$(CC) $(CFLAGS) -c -o $@ $< $(FLAGS)

$(TARGET): $(OBJECTS)
	$(CC) $(LDFLAGS) -o $@ $(OBJECTS) $(FLAGS)

install: $(TARGET)
	cp $(TARGET) $(INSTALL)$(TARGET)

uninstall: $(INSTALL)$(TARGET)
	rm $(INSTALL)$(TARGET)

clean:
	rm -rf *.o
	rm -rf *.so

all: $(SOURCES) $(TARGET)
