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
VPATH	= src

main:	main.c
	$(CC) $(CFLAGS) -o $@ $?


##########################################################
##                      PHONYS                          ##
##########################################################
# Clean
.PHONY: clean
clean:
	rm -rf *.o main
