# You Should Know: C11 Includes a More Secure `strcpy()`

You should know that the C11 update to the C programming language provides replacement “safe” versions of the historically problematic library routines `strcpy()` and `strcat()`.  Using new C11 library functions like `strcpy_s()` is one way to make your code more secure against buffer overflow attacks.

From [Michael Barr blog](https://embeddedgurus.com/barr-code/2017/08/cs-strcpy_s-c11s-more-secure-version-of-strcpy/?utm_medium=email&utm_source=sharpspring&sslid=M7GwMDKwNDGxtLQwAwA&sseid=MzQ1tTAxNDU2MwIA&jobid=39b6d099-3227-4901-94b4-ec142f484c5b):

You should know that the new C11 update to the C programming language provides for a replacement “safe” version of the `strcpy``, which is named `strcpy_s()`. The parameter lists and return types differ:

    char *strcpy(char *strDestination, const char *strSource);

versus:

    errno_t strcpy_s(char *strDestination, size_t numberOfElements, const char *strSource);

The new `numberOfElements` parameter is used by `strcpy_s()` to check that the `strSource` is not bigger than the buffer. And, when there is a problem, an error code is returned.

More information on [MSDN](https://msdn.microsoft.com/en-us/library/td1esda9(v=VS.100).aspx).