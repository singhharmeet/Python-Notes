### MultiProcessing:-

* ***multiprocessing.cpu_count()*** - count the number of cores on a given system, if needed in your code.
* For CPU-bound tasks, it doesn't make sense to create more Pool processes than you have cores to run them on. If you're trying to use your machine for other things too, then you should create fewer processes than cores.
*  For I/O-bound tasks, it may make sense to create a quite a few more Pool processes than cores, since the processes will probably spend most their time blocked (waiting for I/O to complete).
* You can ask for as many processes as you like. Any limit that may exist will be imposed by your operating system, not by multiprocessing
* For each process that you create there is overhead, so you are actually using more memory to do this. 
* ***when we create thread, we use os.fork() which allows us to create a new process by copying everything in the current process into the new process that typically includes everything in memory and the current values of the CPU registers with some minor adjustments. So in effect, the new process gets a copy of the process's instruction pointer as well so it resumes at the same point where the original process would continue***
* after calling os.fork() the parent as well as child program continues parallely with the same memory values (can be copied or referenced to until one process changes the shared value) and carry out the coding based on the timeslices the OS decides to give to each process.
* ***In spawn, The parent process starts a fresh python interpreter process. The child process will only inherit those resources necessary to run the process objects run() method. In particular, unnecessary file descriptors and handles from the parent process will not be inherited.***
* Starting a process using this method is rather slow compared to using fork or forkserver.
* concurrent.futures are not "advanced" as compared to multiprocessing - it's a simpler interface that works very much the same regardless of whether you use multiple threads or multiple processes as the underlying parallelization gimmick.
	* Taken from: https://stackoverflow.com/questions/20776189/concurrent-futures-vs-multiprocessing-in-python-3 
