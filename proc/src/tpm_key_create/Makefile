FLAGS= -g -shared -o
INCLUDE= -I$(CUBESYSPATH)/include/ -I$(CUBELIBPATH)/include
CFLAGS= -g -c -fPIC -DUSER_MODE $(INCLUDE)
CC=gcc
CCP=g++
PLUGIN=tpm_key_create
PLUGIN_OBJ= tpm_key_func.o
TEST_LIB= -L$(CUBELIBPATH)/lib -ltesi -ltspi -lcrypto -lmessage -lmemdb -lconnector -lstruct -lcrypto_func -ljson -lstring -lalloc -lpthread

main: lib$(PLUGIN).so
lib$(PLUGIN).so:  $(PLUGIN).o $(PLUGIN_OBJ) $(INIT_DB_OBJ)
	$(CC) $(FLAGS) lib$(PLUGIN).so $(PLUGIN).o $(PLUGIN_OBJ) $(TEST_LIB)
	mv lib$(PLUGIN).so $(CUBE_SYS_PLUGIN)
	cp $(PLUGIN).cfg $(CUBE_SYS_PLUGIN)
$(PLUGIN).o: $(PLUGIN).c $(PLUGIN).h
	$(CC) $(CFLAGS) $(PLUGIN).c
tpm_key_func.o:tpm_key_func.c
	$(CC) $(CFLAGS) tpm_key_func.c
	
clean:
	rm -f lib$(PLUGIN).so 
	rm  *.o *~
