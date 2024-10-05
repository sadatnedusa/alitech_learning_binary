# Named pipes.

- Named pipes, also known as FIFOs (First In, First Out), are a special type of inter-process communication (IPC) mechanism in Unix-like operating systems,including Linux.
- Unlike unnamed pipes, named pipes have a name and can be accessed by multiple processes, allowing for more flexible communication.

## What Are Named Pipes?

- **Definition**: Named pipes are a type of pipe that has a specific name and can be accessed like a regular file. They allow for communication between processes that do not have a parent-child relationship.
- **Characteristics**:
  - **Persistent**: Named pipes persist in the file system until they are explicitly deleted. They do not disappear when the processes using them terminate.
  - **Bidirectional**: Named pipes can be used to send and receive data, although the data still flows in a first-in, first-out (FIFO) manner.
  - **Blocking Behavior**: Similar to unnamed pipes, if the reading process is not ready to read data from the pipe, the writing process will block until the data is consumed.

### How to Create a Named Pipe

You can create a named pipe using the `mkfifo` command in the terminal.

**Syntax**:
```bash
mkfifo <pipe_name>
```

### Example of Using Named Pipes

#### Step 1: Create a Named Pipe

First, create a named pipe using `mkfifo`:

```bash
mkfifo mypipe
```

This command creates a named pipe called `mypipe` in the current directory.

#### Step 2: Writing to the Named Pipe

You can write to the named pipe using any command. For example, you can use the `echo` command:

Open a terminal and run:
```bash
echo "Hello, World!" > mypipe
```

This command sends the string "Hello, World!" into the `mypipe`.

#### Step 3: Reading from the Named Pipe

In another terminal, you can read from the named pipe using the `cat` command:

```bash
cat < mypipe
```

When you run this command, it will block and wait for data to be written into the pipe. Once you execute the `echo` command from the previous step, it will output:

```
Hello, World!
```

### Example with Multiple Processes

Named pipes can facilitate communication between different processes. Here’s an example using two different terminal windows:

#### Terminal 1: Write to the Named Pipe

In Terminal 1, start a command to write data to the named pipe:

```bash
echo "Data from Process 1" > mypipe
```

#### Terminal 2: Read from the Named Pipe

In Terminal 2, start a command to read from the named pipe:

```bash
cat < mypipe
```

When you execute the echo command in Terminal 1, Terminal 2 will immediately display:

```
Data from Process 1
```

#### Additional Example: Using `cat` and `grep`

You can also use named pipes with commands like `cat` and `grep`. For instance, you can create a named pipe and use it to filter output:

1. Create a named pipe:
   ```bash
   mkfifo mypipe
   ```

2. Open a terminal and run `cat` to read from the named pipe:
   ```bash
   cat < mypipe | grep "banana"
   ```

3. In another terminal, write data to the named pipe:
   ```bash
   echo -e "apple\nbanana\ncherry" > mypipe
   ```

In this example, the `cat` command reads the data from the named pipe and pipes it to `grep`, which filters out only the line containing "banana". The output will be:

```
banana
```

### Advantages of Named Pipes

1. **Flexibility**: Named pipes allow unrelated processes to communicate with each other, unlike unnamed pipes, which are limited to related processes.
  
2. **Persistence**: Named pipes persist in the filesystem until deleted, enabling processes to communicate at different times.

3. **File System Integration**: Named pipes are treated as files, allowing for the use of standard file operations.

### Points to Ponder.

- Named pipes (FIFOs) are a powerful IPC mechanism in Linux that allows for flexible and persistent communication between processes.
- They provide a simple way to transfer data using standard file operations, making them easy to integrate into scripts and applications.
- The examples provided demonstrate how to create, write to, and read from named pipes, showcasing their versatility in various scenarios.
