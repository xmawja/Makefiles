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
TESDIR  = test
PREDIR	= pros
CMPDIR	= comp
OBJDIR	= obj
BINDIR	= bin
DEPDIR	= dep
DATDIR	= data
DOCDIR	= doc
# Organize directorys
APPDIR	= $(SRCDIR) $(HDRDIR) $(TESDIR)
BLDDIR	= $(DEPDIR) $(OBJDIR)
# Search for the directorys
VPATH	= $(APPDIR) $(BLDDIR) 

# All target variable
all:    $(TARGET)

# declaration variables
RM	= rm -f
RMDIR	= rm -rf
# Directorys variables
SOURCES	:= $(wildcard $(VPATH)/*.c)
HEADERS := $(wildcard $(VPATH)/*.h)
PREPROS	:= $(SOURCES:$(SRCDIR)/%.c=$(PREDIR)/$.c)
COMPILE := $(SOURCES:$(PREDIR)/$.c=$(CMPDIR)/$.s)
OBJECTS	:= $(SOURCES:$(CMPDIR)/%.s=$(OBJDIR)/%.o)
DEPS	:= $(OBJECTS:$(OBJDIR)/%.o=$(DEPDIR)/%.d)

##########################################################
##                      COMPILATION                     ##
##########################################################
# Preprocessing
$(PREPROS): $(SRCDIR)/%.c : $(PREDIR)/%.c
	mkdir -p $(PREDIR)
	$(CC) $(CFLAGS) -E -o $(DEPDIR)/%.c $(VPATH)/$.c
	@echo "Preprocessing ... $<"

# Comilation
$(COMPILE): $(PREDIR)/$.c : $(CMPDIR)%.s
	mkdir -p $(CMPDIR)
	$(CC) $(CFLAGS) -S $^
	@echo "Compiling ... $<"

# Assembling
$(OBJECTS): $(CMPDIR)%.s : $(HEADERS)%.h
	mkdir -p $(OBJDIR)
	$(CC) $(CFLAGS) -c $^
	@echo "Assembling ... $<"

# Linking
$(BINDIR)/$(TARGET): $(OBJECTS)
	mkdir -p $(BINDIR)
	$(CC) $(CFLAGS) $(OBJECTS) -o $@
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
	$(RM) $(OBJECTS) $(OBJDIR) $(BINDIR) $(DEPDIR)
	@echo "Deleted ...$<"

# remove all target with deps 
.PHONY: remove
remove:
	$(RMDIR) $(BINDIR)/$(TARGET)
	$(RMDIR) $(OBJECTS)
	$(RMDIR) $(DEPS)
	@echo "Deleted $<"

# PHONY target variables
.PHONY: all
