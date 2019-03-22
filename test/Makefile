TARGET = test
vpath %.c ./atcacert:./jwt
SRC = cmd-processor.c atca_crypto_sw_tests.c atca_test.c atca_tests_aes.c \
atca_tests_aes_cbc.c atca_tests_aes_cmac.c atca_tests_aes_ctr.c atca_tests_aes_gcm.c \
atca_tests_helper.c atca_tests_hmac.c atca_tests_info.c atca_tests_kdf.c \
atca_tests_lock.c atca_tests_mac.c atca_tests_nonce.c atca_tests_otpzero.c \
atca_tests_pause.c atca_tests_privwrite.c atca_tests_random.c atca_tests_read.c \
atca_tests_secureboot.c atca_tests_selftest.c atca_tests_sha.c atca_tests_sign.c \
atca_tests_startup.c atca_tests_updateextra.c atca_tests_verify.c atca_tests_write.c \
atca_utils_sizes.c unity.c unity_fixture.c \
all_atcacert_tests.c test_atcacert_client.c test_atcacert_client_runner.c \
test_atcacert_date.c test_atcacert_date_runner.c test_atcacert_def.c \
test_atcacert_def_runner.c test_atcacert_der_ecdsa_sig_value.c test_atcacert_der_ecdsa_sig_value_runner.c\
test_atcacert_der_integer.c test_atcacert_der_integer_runner.c test_atcacert_der_length.c \
test_atcacert_der_length_runner.c test_atcacert_host_hw.c test_atcacert_host_hw_runner.c \
test_cert_def_0_device.c test_cert_def_1_signer.c test_cert_def_2_device_csr.c \
atca_jwt_test.c 
         
CFLAGS = -Wall -O3  
INCLUDE = -I../lib -I../ 
LDFLAGS = -lpthread 
LIBS = -L../lib/build/ -lcryptoauth -L./atcacert -L./jwt
CC = gcc     
      
MAKEFLAGS += -rR --no-print-directory

DEP_CFLAGS = -MD -MP -MQ $@
    
OBJ = $(addsuffix .o,$(basename $(SRC)))
DEP = $(addsuffix .d,$(basename $(SRC)))
    
.PHONY: clean all
    
all: $(TARGET)
$(TARGET): $(OBJ)
        $(CC) $(LDFLAGS) $(OBJ) $(LIBS) -o $@

clean:
        rm -f $(OBJ)
        rm -f $(DEP)
        rm -f $(TARGET)

%.o: %.c
        $(CC) $(DEP_CFLAGS) $(INCLUDE) $(CFLAGS) -c $< -o $@

include $(wildcard $(DEP))
