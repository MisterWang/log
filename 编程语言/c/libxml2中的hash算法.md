```c
unsigned long has_code(char* name){
  unsigned long value = 0L;

  if (name != NULL) {
	while (*name) {
	    value = value ^ ((value << 5) + (value >> 3)) + *name++;
	}
  }

  return value;
}

```
