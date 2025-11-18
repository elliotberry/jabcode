PREFIX   =
CC       = $(PREFIX)gcc
CFLAGS   = -O2 -std=c11
CPPFLAGS = -I/opt/homebrew/include
LDFLAGS  = -L/opt/homebrew/lib

TARGET   = bin/jabcodeWriter
OBJECTS  = $(patsubst %.c,%.o,$(wildcard *.c))

$(TARGET): $(OBJECTS)
	$(CC) $^ \
		-L../jabcode/build -ljabcode \
		-L../jabcode/lib -ltiff -lpng16 -lz -lm \
		$(LDFLAGS) -lzstd -llzma -ljpeg \
		$(CFLAGS) -o $@

$(OBJECTS): %.o: %.c
	$(CC) -c -I. -I../jabcode -I../jabcode/include $(CPPFLAGS) $(CFLAGS) $< -o $@

clean:
	rm -f $(TARGET) $(OBJECTS)