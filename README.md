# C++ cheatsheet

## Basic pointer stuff
```
int x = 0;
int *p = &x;

printf("x: %d, &x: %p, p: %p, *p: %d\n", x, &x, p, *p);

Output:
x: 0, &x: 0x7fff5a0e92a4, p: 0x7fff5a0e92a4, *p: 0
```

### Slightly less basic pointer stuff
```
std::vector<particle_t*>* boxes[num_boxes];
for (int i = 0; i < num_boxes; i++ )
{
    boxes[i] = new std::vector<particle_t*>;
}

std::vector<particle_t*> bin = *boxes[0];
printf("&bin: %p, &boxes[0]: %p\n", &bin, &boxes[0]);
if (bin.size() > 0) {
  printf("&bin: %p, bin[0]: %p, &boxes[0]: %p\n", &bin, bin[0], &boxes[0]);
  printf("&bin: %p, bin[0]: %p, &boxes[0]: %p (*boxes[0])[0]: %p\n", &bin, bin[0], &boxes[0], (*boxes[0])[0]);
  
  // note: this doesn't work: error: indirection requires pointer operand ('std::vector<particle_t *>' invalid) 
  printf("&bin: %p, bin[0]: %p, &boxes[0]: %p *boxes[0][0]: %p\n", &bin, bin[0], &boxes[0], *boxes[0][0]);
}

Output (printed on different runs):
&bin: 0x7fff53ee8268, &boxes[0]: 0x7fff53ee7ff0
&bin: 0x7fff5159b268, bin[0]: 0x7f8601c03270, &boxes[0]: 0x7fff5159aff0
&bin: 0x7fff594c8258, bin[0]: 0x7f804b4032a0, &boxes[0]: 0x7fff594c7fd0 (*boxes[0])[0]: 0x7f804b4032a0

```
