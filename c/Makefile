##########################################################
##			GENERALS			##
##########################################################
# Compiler target
CC	= cc
# Compiling flags
CFLAGS	= -Wall -Wextra -Werror
# Linking flags
LFLAGS	=
# Libraries flags
LDFLAGS	=

##########################################################
##			PROJECTS			##
##########################################################
# Name
TARGET	= name
# Directorys
SRCDIR	= src
HDRDIR	= inc
OBJDIR	= obj
BINDIR	= bin
DEPDIR	= dep
DATDIR	= data
DOCDIR	= doc
TESDIR	= test

# All target variable
all:    $(TARGET)

# declaration variables
RM	= rm -f
RMDIR	= rm -rf
# Directorys variables
SOURCES	:= $(wildcard $(SRCDIR)/*.c)
HEADERS := $(wildcard $(HDRDIR)/*.h)
OBJECTS	:= $(SOURCES:$(SRCDIR)/%.c=$(OBJDIR)/%.o)
DEPS	:= $(OBJECTS:$(OBJDIR)/%.o=$(DEPDIR)/%.d)

##########################################################
##                      COMPILATION                     ##
##########################################################
# Preprocessing
pre:
	mkdir -p $(DEPDIR)
	$(CC) $(CFLAGS) -E -o main_expanded.c main.c
	@echo "Preprocessing ..."

# Comilation
cop: main_expanded.c
	$(CC) $(CFLAGS) -S $^
	@echo "Compiling ..."

# Assembling
%.o: %.c %.h
	mkdir -p $(OBJDIR)
	$(CC) $(CFLAGS) -c $^
	@echo "Assembling ..."

# Linking
$(TARGET): main.o
	mkdir -p $(BINDIR)
	$(CC) $(CFLAGS) main.o -o $@
	@echo "Linking ..."

##########################################################
##                      PHONYS                          ##
##########################################################
# Test
.PHONY: test
test:
	$()

# Clean
.PHONY: clean
clean:
	$(RM) *.o $(TARGET)
	
# remove
.PHONY: remove
remove:
	$(RMDIR) $(OBJDIR) $(BINDIR)

# PHONY target variables
.PHONY: all
