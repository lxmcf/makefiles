# ----------------------------------------------------------------------------------
# CONFIG
# ----------------------------------------------------------------------------------
EXE ?= application
BUILD ?= BUILD_DEBUG

CC := gcc
COMPILER_FLAGS := -O2 -Wall
LINKER_FLAGS := -lm
SRC_FILES := $(wildcard src/*.c) $(wildcard src/*/*.c)
DEFINES :=

# ----------------------------------------------------------------------------------
# OS SETUP
# ----------------------------------------------------------------------------------
EXE_EXT :=

ifeq ($(OS), Windows_NT)
	EXE_EXT := .exe
endif

# ----------------------------------------------------------------------------------
# CONFIG SETUP
# ----------------------------------------------------------------------------------
ifeq ($(BUILD), BUILD_DEBUG)
	COMPILER_FLAGS += -g
	DEFINES += -DBUILD_DEBUG
endif

# ----------------------------------------------------------------------------------
# TARGETS
# ----------------------------------------------------------------------------------
.PHONY: build run clean release

build: $(EXE)$(EXE_EXT)

$(EXE)$(EXE_EXT): $(SRC_FILES)
	$(CC) $(DEFINES) $^ $(COMPILER_FLAGS) $(LINKER_FLAGS) -o $@

run: build
	./$(EXE)$(EXE_EXT)

clean:
	rm -f $(EXE)$(EXE_EXT)

release: build
	zip -r $(EXE)$(EXE_EXT)
