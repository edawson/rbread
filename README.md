
# rbread.h

Header-only, gzread-like reader for gzip, bz2, and xz.

## Example

```C
#include "rbread.h"

/* simple zcat / bzcat */
int dump_file(char const *filename, FILE *out)
{
	rbread_t *rb = rbopen(filename);		/* always in read mode; "rb" for plain text */
	if(rb == NULL) { return(1); }
	while(rbeof(rb) == 0) {
		size_t read = rbread(rb, buf, buf_size);
		fwrite(buf, 1, read, out);
	}
	rbclose(rb);
	fflush(out);
	return(0);
}
```

## License

MIT

Copyright (2018), Hajime Suzuki
