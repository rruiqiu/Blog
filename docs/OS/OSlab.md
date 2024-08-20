# OS Lab

## Lab1: Xv6 and Unix utilities

## Lab2: system calls

## Lab3: page tables

The lab manual can be found here.https://pdos.csail.mit.edu/6.828/2021/labs/pgtbl.html

### Speed up system calls ([easy](https://pdos.csail.mit.edu/6.828/2021/labs/guidance.html))

Purpose: speed up certain system calls by sharing data in a read-only region between user space and the kernel. This task is to map one read-only page at USYSCALL( a virtual address defined in memlayout.h). At the start of this page, store a `struct usyscall` (also defined in `memlayout.h`), and initialize it to store the PID of the current process.

```c
//proc.h
struct proc {
  struct spinlock lock;

  // p->lock must be held when using these:
  enum procstate state;        // Process state
  void *chan;                  // If non-zero, sleeping on chan
  int killed;                  // If non-zero, have been killed
  int xstate;                  // Exit status to be returned to parent's wait
  int pid;                     // Process ID

  // wait_lock must be held when using this:
  struct proc *parent;         // Parent process

  // these are private to the process, so p->lock need not be held.
  uint64 kstack;               // Virtual address of kernel stack
  uint64 sz;                   // Size of process memory (bytes)
  pagetable_t pagetable;       // User page table
  struct trapframe *trapframe; // data page for trampoline.S
  struct context context;      // swtch() here to run process

  struct file *ofile[NOFILE];  // Open files
  struct inode *cwd;           // Current directory
  char name[16];               // Process name (debugging)
  // add the struct to store the shared page table
  struct usyscall *usyscall;   //get pid
};

//proc.c
static struct proc*
allocproc(void)
{
  struct proc *p;

  for(p = proc; p < &proc[NPROC]; p++) {
    acquire(&p->lock);
    if(p->state == UNUSED) {
      goto found;
    } else {
      release(&p->lock);
    }
  }
  return 0;

found:
  p->pid = allocpid();
  p->state = USED;


  // Allocate a trapframe page.
  if((p->trapframe = (struct trapframe *)kalloc()) == 0){
    freeproc(p);
    release(&p->lock);
    return 0;
  }
  //Allocate a USYSCALL page, my implementation
  if((p->usyscall = (struct usyscall *)kalloc()) == 0){
    freeproc(p);
    release(&p->lock);
    return 0;
  }
  //share the pid between userspace and the kernel
  p->usyscall->pid = p->pid;
  // An empty user page table.
  p->pagetable = proc_pagetable(p);
  if(p->pagetable == 0){
    freeproc(p);
    release(&p->lock);
    return 0;
  }

  // Set up new context to start executing at forkret,
  // which returns to user space.
  memset(&p->context, 0, sizeof(p->context));
  p->context.ra = (uint64)forkret;
  p->context.sp = p->kstack + PGSIZE;

  return p;
}


// Create a user page table for a given process,
// with no user memory, but with trampoline pages.
pagetable_t
proc_pagetable(struct proc *p)
{
  pagetable_t pagetable;

  // An empty page table.
  pagetable = uvmcreate();
  if(pagetable == 0)
    return 0;

  // map the trampoline code (for system call return)
  // at the highest user virtual address.
  // only the supervisor uses it, on the way
  // to/from user space, so not PTE_U.
  if(mappages(pagetable, TRAMPOLINE, PGSIZE,
              (uint64)trampoline, PTE_R | PTE_X) < 0){
    uvmfree(pagetable, 0);
    return 0;
  }

  // map the trapframe just below TRAMPOLINE, for trampoline.S.
  if(mappages(pagetable, TRAPFRAME, PGSIZE,
              (uint64)(p->trapframe), PTE_R | PTE_W) < 0){
    uvmunmap(pagetable, TRAMPOLINE, 1, 0);
    uvmfree(pagetable, 0);
    return 0;
  }

  //create a page for usyscall and map with READ only and also allow it to be accessed by the USER.
  if(mappages(pagetable, USYSCALL, PGSIZE,
              (uint64)(p->usyscall), PTE_R | PTE_U) < 0){
    uvmunmap(pagetable, TRAMPOLINE, 1, 0);
    uvmunmap(pagetable, TRAPFRAME, 1, 0);
    uvmfree(pagetable, 0);
    return 0;
  }

  return pagetable;
}

// Don't forget to free the leaf of the USYSCALL page, else it will cause a leaf panic error
// Free a process's page table, and free the
// physical memory it refers to.
void
proc_freepagetable(pagetable_t pagetable, uint64 sz)
{
  uvmunmap(pagetable, TRAMPOLINE, 1, 0);
  uvmunmap(pagetable, TRAPFRAME, 1, 0);
  uvmunmap(pagetable, USYSCALL, 1, 0);
  uvmfree(pagetable, sz);
}
```

### Print a page table ([easy](https://pdos.csail.mit.edu/6.828/2021/labs/guidance.html))

Purpose: Print the contents of a page table

Define a function called `vmprint()`. It should take a `pagetable_t` argument, and print that pagetable in the format described below. Insert `if(p->pid==1) vmprint(p->pagetable)` in exec.c just before the `return argc`, to print the first process's page table. You receive full credit for this part of the lab if you pass the `pte printout` test of `make grade`.

```c


//vm.c
//use recursion to print the pte on page tables
void vmprint(pagetable_t pagetable,int r)
{
  // r =0. first r
  char *format ="";
  if(r == 0){
    pte_t pa = (uint64)pagetable;
    printf("page table %p\n",pa);
    format = "..";
    r++;
  }else if(r ==1){
    format = ".. ..";
    r++;
  }else if(r==2){
    format = ".. .. ..";
    r++;
  }

  for(int i=0;i<512;i++){
    pte_t pte = pagetable[i];
    //if there is a valid page
    if((pte & PTE_V) && (pte & (PTE_R|PTE_W|PTE_X)) == 0){
      // this PTE points to a lower-level page table.

      //PTE2PA will get the next page PA address
      uint64 child = PTE2PA(pte);
      printf("%s%d: pte %p pa %p\n",format,i,pte,child);
      // printf("child %p\n",child);
      vmprint((pagetable_t)child,r);
    } else if(pte & PTE_V){	//these are the leaf of the page
      uint64 child = PTE2PA(pte);
      printf("%s%d: pte %p pa %p\n",format,i,pte,child);

    }
  }

}


//exec.c
//add this code in int exec(char *path, char **argv) before the return argument to allow it to print the page table when the pid is 1
  if(p->pid ==1) vmprint(p->pagetable,0);

```

### Detecting which pages have been accessed ([hard](https://pdos.csail.mit.edu/6.828/2021/labs/guidance.html))

Purpose: Based on the input arguments, determine which pages have been accessed(read or write).

Your job is to implement `pgaccess()`, a system call that reports which pages have been accessed. The system call takes three arguments. First, it takes the starting virtual address of the first user page to check. Second, it takes the number of pages to check. Finally, it takes a user address to a buffer to store the results into a bitmask (a datastructure that uses one bit per page and where the first page corresponds to the least significant bit). You will receive full credit for this part of the lab if the `pgaccess` test case passes when running `pgtbltest`.

![image-20240820010655487](./OSlab.assets/image-20240820010655487.png)

```c
//riscv.h
#define PTE_A (1L << 6) //Access Bit

//sysproc.c

#ifdef LAB_PGTBL
int
sys_pgaccess(void)
{
  //parse arugments
  uint64 va;
  int num;
  uint64 buffer; //buffer to store the result in bitmask ds
  int ans = 0;
  if(argaddr(0,&va) < 0) return -1;
  if(argint(1,&num)<0) return -1;
  if(argaddr(2,&buffer)<0) return -1;

  struct proc *p = myproc(); //get the current process status
  pagetable_t pagetable = p->pagetable; //the user page table

  for(int i=0;i<num;i++){
    pte_t *pte;
    pte = walk(pagetable,va+ (i * PGSIZE),0);

    if((pte != 0) && (*pte & PTE_A)){
      ans = ans | (1 << i);
      *pte = *pte ^ PTE_A;
    }
  }
  //copy the answer from kernel to the user space, stored in the third input argument ans,
    //copy byte by byte
  if(copyout(pagetable,buffer,(char *)&ans,sizeof(int)) < 0){
    return -1;
  }
  return 0;
//pgaccess(buf, 32, &abits)

}
#endif

```

### Bitmask data structure:

Bitmask Basics:

- **Representation**: A bitmask is typically represented as an integer where each bit corresponds to a specific option, flag, or element.
  - For example, an 8-bit bitmask can represent up to 8 different flags or states, with each bit in the byte being either `0` (off/false) or `1` (on/true).
- **Efficiency**: Bitmasks are efficient because they allow you to represent multiple states or flags within a single integer, using very little memory (e.g., 1 byte can store 8 flags).
- **Common Uses**:
  - **Flags**: In many programming languages, bitmasks are used to store flags, where each bit in the bitmask represents a different flag.
  - **Permissions**: Bitmasks are often used to store permission bits, where each bit represents a different permission (e.g., read, write, execute).
  - **Presence of Elements**: In algorithms, bitmasks can be used to represent whether certain elements or conditions are present.

### Explanation of Byte Pointer:

- **Pointer Basics**:

  - A pointer is a variable that holds the memory address of another variable.
  - The type of the pointer determines how the memory is accessed. For example, an `int*` pointer is expected to point to an `int` and thus access 4 bytes of memory (on most systems), whereas a `char*` pointer (byte pointer) accesses 1 byte of memory.

- **Byte Pointer (`char\*`)**:
  - A `char*` or `unsigned char*` pointer is often referred to as a byte pointer because `char` typically represents a single byte (8 bits) of data.
  - With a byte pointer, you can perform fine-grained memory operations, such as accessing and modifying memory byte by byte.

#### Example of Byte Pointer Usage:

Consider a scenario where you have an integer value, but you want to access or manipulate its bytes individually:

```c
#include <stdio.h>

int main() {
    int num = 0x12345678;   // A 4-byte integer
    char *byte_ptr = (char*)&num;  // Cast the address of num to a byte pointer

    // Access and print each byte of the integer
    for(int i = 0; i < sizeof(int); i++) {
        printf("Byte %d: 0x%x\n", i, byte_ptr[i]);
    }

    return 0;
}
```

#### Explanation:

- Memory Representation
  - `num` is a 4-byte integer. Its value `0x12345678` will be stored in memory as four bytes: `0x12`, `0x34`, `0x56`, `0x78`.
- Pointer Cast
  - `char* byte_ptr = (char*)#` converts the address of `num` (which is an `int*`) to a `char*`, allowing you to access the individual bytes of the integer.
- Byte-by-Byte Access
  - `byte_ptr[i]` accesses the `i`-th byte of `num`. Since `byte_ptr` is a `char*`, `byte_ptr[i]` accesses the memory one byte at a time.

#### Output:

```c
Byte 0: 0x78
Byte 1: 0x56
Byte 2: 0x34
Byte 3: 0x12
```

#### Why Use a Byte Pointer?

- **Memory Manipulation**: Byte pointers are useful when you need to manipulate data at a low level, such as copying raw memory, accessing specific bytes in a larger data structure, or working with binary data formats.
- **Typecasting**: Often, you might cast a higher-level pointer (e.g., `int*`, `float*`) to a `char*` to inspect or manipulate its bytes, as seen in the example above.

### Summary

I enhance some interesting things that i never notice before, `copyout(pagetable,buffer,(char *)&ans,sizeof(int))` this function is actually copying the data byte by byte, and it is a really useful technique if we want to write a generic function that accept different data types arguments and perform the copy. Idea is in C, the data type will define how many bytes of memory to read, let's say if the data type is int _, then it will read 4 bytes contiguous memory blocks. And since char _ only has the one byte(lowest), it will be safe to copy those memory blocks byte by byte and later cast those address to the original data type.

## Lab4: traps
