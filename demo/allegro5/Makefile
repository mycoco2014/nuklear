# Install
BIN = demo

# Compiler
CC = clang
DCC = gcc

# Flags
CFLAGS = -std=c89 -pedantic

SRC = main.c
OBJ = $(SRC:.c=.o)

ifeq ($(OS),Windows_NT)
BIN := $(BIN).exe
LIBS = -lmingw32 -lallegro -lallegro_primitives -lm
else
	UNAME_S := $(shell uname -s)
	ifeq ($(UNAME_S),Darwin)
		LIBS = -lallegro -lallegro_primitives -lallegro_main -framework OpenGL -lm -lGLEW
	else
		LIBS = -lallegro -lallegro_primitives -lallegro_main -lGL -lm -lGLU -lGLEW
	endif
endif

# Modes
.PHONY: gcc
gcc: CC = gcc
gcc: $(BIN)

.PHONY: clang
clang: CC = clang
clang: $(BIN)

$(BIN):
	@mkdir -p bin
	rm -f bin/$(BIN) $(OBJS)
	$(CC) $(SRC) $(CFLAGS) -o bin/$(BIN) $(LIBS)
