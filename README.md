
# 64 bit and up integer routines for the ez80 microprocessor
Simulated 64 bit and up integer arithmetic for a 24 bit processor (WIP)

+ Author: Adam "beckadamtheinventor" Beckingham
+ License: GPL3

# 64-bit unsigned integer arithmetic functions

Allocate a 64-bit integer using a custom malloc function.

`ce_uint64_t *u64_alloc(void* (*_alloc)(size_t));`

Allocate a 64-bit integer using malloc.

`#define u64_malloc() malloc(8)`

Zero a 64-bit integer.

`ce_uint64_t *u64_zero(ce_uint64_t *A);`

Convert a 24-bit unsigned integer B, storing to 64-bit unsigned integer A.

`ce_uint64_t *u64_ito64(ce_uint64_t *A, unsigned int B);`

Convert a 24-bit signed integer B, storing to 64-bit signed integer A.

`ce_int64_t *i64_ito64(ce_int64_t *A, int B);`

Shift a 64-bit integer A by B bits left.

`ce_uint64_t *u64_shl(ce_uint64_t *A, uint8_t B);`

Shift a 64-bit integer A by B bits right.

`ce_uint64_t *u64_shr(ce_uint64_t *A, uint8_t B);`

Invert a 64-bit signed integer.

`ce_int64_t *i64_invert(void);`

Add a 64-bit integer A and B, storing to A.

`ce_uint64_t *u64_add(ce_uint64_t *A, ce_uint64_t *B);`

Add a 64-bit integer A and 24-bit integer B, storing to A.

`ce_uint64_t *u64_addi(ce_uint64_t *A, unsigned int B);`

Multiply two 64-bit integers A and B, storing to A.

`ce_uint64_t *u64_mul(ce_uint64_t *A, ce_uint64_t *B);`

Subtract two 64-bit integers A minus B, storing to A.

`ce_uint64_t *u64_sub(ce_uint64_t *A, ce_uint64_t *B);`

Subtract two 64-bit integers A minus 24-bit integer B, storing to A.

`ce_uint64_t *u64_subi(ce_uint64_t *A, unsigned int B);`

Divide 64-bit integer A by 64-bit integer B, storing result to A and remainder to R.

`ce_uint64_t *u64_div(ce_uint64_t *A, ce_uint64_t *B, ce_uint64_t *R);`

Copy a 64-bit integer from src to dest. Returns pointer to dest.

`ce_uint64_t *u64_copy(ce_uint64_t *dest, ce_uint64_t *src);`

Convert a 64-bit integer to a hex string. buf must be allocated at least 17 bytes.

`char *u64_tohex(char *buf, ce_uint64_t *A);`


# 64-bit signed integer arithmetic routines

Add a 24 bit signed integer B to a 64-bit signed integer A.

`ce_int64_t *i64_addi(ce_int64_t *A, int B);`

Subtract a 24 bit signed integer B from a 64-bit signed integer A.

`ce_int64_t *i64_subi(ce_int64_t *A, int B);`

Convert a 24 bit signed integer B to a 64-bit signed integer A.

`ce_int64_t *i64_ito64(ce_int64_t *A, int B);`

Compare two signed 64-bit integers A and B. Currently synonomous with u64_cmp.

`uint8_t i64_cmp(ce_int64_t *A, ce_int64_t *B);`

Unary negate 64 bit signed integer A, returning A = ~A.

`ce_int64_t *i64_neg(ce_int64_t *A);`

Convert a 64 bit signed integer A to a hexadecimal string buf. buf must be allocated at least 18 bytes to account for
negative integer inputs outputting an extra character '-' prepending the output.

`char *i64_tohex(char *buf, ce_int64_t *A);`

# variable-length integer arithmetic routines

allocate a variable-length integer. Size in *bytes*, not bits.
Example usage:

	`vint_alloc(16, malloc);`
Minimum number of bytes is 4.

`vint_t *vint_alloc(uint8_t bytes, void*(void(*_alloc)(size_t)));`

allocate a variable length integer using malloc. See vint_alloc for more information.

`#define vint_malloc(a) vint_alloc(a, malloc)`

Zero a variable-length integer.

`vint_t *vint_zero(vint_t *A);`

Add two variable-length integers A and B, storing to A.

`vint_t *vint_add(vint_t *A, vint_t *B);`

Add a variable-length integer A and an unsigned 24-bit integer B, storing to A.

`vint_t *vint_addi(vint_t *A, unsigned int B);`

Subtract a variable-length integer B from A, storing to A.

`vint_t *vint_sub(vint_t *A, vint_t *B);`

Subtract an unsigned integer B from a variable-length integer A, storing to A.

`vint_t *vint_subi(vint_t *A, unsigned int B);`

Convert an unsigned 24-bit integer to a variable-length integer

`vint_t *vint_itov(vint_t *A, unsigned int B);`

Copy variable length integer src to dest. src and dest do not need to be the same length.

`vint_t *vint_copy(vint_t *dest, vint_t *src);`

Convert a variable-length integer to a hex string. buf must be allocated at least len(A)*2 + 1 bytes.

`char *vint_tohex(char *buf, vint_t *A);`

