CC ?= /usr/bin/cc

CFLAGS += -Wall -Wextra -Wpedantic -Wmissing-prototypes -Wredundant-decls \
  -Wshadow -Wpointer-arith -O3 -std=c11 -march=native -mtune=native \
  -mavx2 -mpopcnt -maes -mbmi2
NISTFLAGS += -Wno-unused-result -O3 -mavx2 -mpopcnt -maes -mbmi2 \
  -march=native -mtune=native
SOURCES = aes.c blas_comm.c blas_matrix_avx2.c blas_matrix_sse.c blas_matrix.c \
		fips202.c gf16.c mqs_keypair_computation_simd.c mqs_keypair_computation.c mqs_keypair.c \
		mqs_simd.c parallel_matrix_op_avx2.c parallel_matrix_op.c rng.c sign.c utils_hash.c utils_prng.c
HEADERS = aes.h api.h blas_avx2.h blas_comm.h blas_config.h blas_matrix_avx2.h crypto_declassify.h \
		blas_matrix_sse.h blas_matrix.h blas_sse.h blas.h fips202.h gf16_avx2.h \
		gf16_sse.h gf16_tabs.h gf16_u64.h gf16.h hash_len_config.h mpkc_avx2.h mpkc.h mqs_blas_simd.h \
		mqs_blas.h mqs_config.h mqs_keypair_computation_simd.h mqs_keypair_computation.h mqs_keypair.h \
		mqs.h parallel_matrix_op_avx2.h parallel_matrix_op.h rng.h utils_hash.h utils_malloc.h utils_prng.h

.PHONY: all test_speed PQCgenKAT_sign clean

all: \
	test_speed \
	PQCgenKAT_sign

test_speed: \
	test/test_speed1 \
	test/test_speed3 \
	test/test_speed5

PQCgenKAT_sign: \
	PQCgenKAT_sign1 \
	PQCgenKAT_sign3 \
	PQCgenKAT_sign5

test/test_speed1: test/test_speed.c $(SOURCES) $(HEADERS)
	$(CC) $(CFLAGS) -D_MQS256_72_46 \
		-o $@ $< $(SOURCES)

test/test_speed3: test/test_speed.c $(SOURCES) $(HEADERS)
	$(CC) $(CFLAGS) -D_MQS256_112_72 \
		-o $@ $< $(SOURCES)

test/test_speed5: test/test_speed.c $(SOURCES) $(HEADERS)
	$(CC) $(CFLAGS) -D_MQS256_148_96 \
		-o $@ $< $(SOURCES)

PQCgenKAT_sign1: PQCgenKAT_sign.c $(SOURCES) $(HEADERS)
	$(CC) $(NISTFLAGS) -D_MQS256_72_46 \
		-o $@ $< $(SOURCES)

PQCgenKAT_sign3: PQCgenKAT_sign.c $(SOURCES) $(HEADERS)
	$(CC) $(NISTFLAGS) -D_MQS256_112_72 \
		-o $@ $< $(SOURCES)

PQCgenKAT_sign5: PQCgenKAT_sign.c $(SOURCES) $(HEADERS)
	$(CC) $(NISTFLAGS) -D_MQS256_148_96 \
		-o $@ $< $(SOURCES)

clean:
	rm -f test/test_speed1
	rm -f test/test_speed3
	rm -f test/test_speed5
	rm -f PQCgenKAT_sign1
	rm -f PQCgenKAT_sign3
	rm -f PQCgenKAT_sign5


