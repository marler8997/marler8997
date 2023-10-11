# Makefiles Suck

Here's how makefiles work:

```make
output1 output2: input1 input2
    command1...
    command2...
```

The developer is responsible for correctly specifying all inputs/outputs correctly.
The problem is that the input list can be incorrect.
Here's another way makefiles could work:

```make
name:
    command1...
    command2...
```

In this case the Make program will run every command but with a way to audit/monitor every file that the commands read from or write to.  Make will create a depsfile with these inputs/outputs and use that to faciliate when rebuilds need to be done.
