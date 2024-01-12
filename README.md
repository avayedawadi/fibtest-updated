# Fibtest

## My (Avaye Dawadi's) changes
This code was written originally written by IndeedEng when Linux was still on cgroup v1 but I re-wrote this to work with cgroup v2 conventions (please 
refer to kernel documentation for differences between v1 and v2). If something is wrong or could be made better, feel free
to make a pull request.

To Be Dones:
- Show the throttled percentage value
- Figure out how to make this work with being able to choose your own scheduler using chrt, it would be cool to see how things are different based on different scheduling algorithms but the throttled data just shows as 0 when using chrt.

![OSS Lifecycle](https://img.shields.io/osslifecycle/indeedeng/fibtest.svg)

Fibtest is a small C application that runs the Fibonacci sequence and reports
how many iterations it completed.

It spawns fast threads and slow threads.  Fast threads run the sequence as fast
as possible.  Slow threads run 100 iterations and then sleep for 10ms.  Each
thread is pinned to its corresponding CPU (thread 0 is on CPU 0, thread 2 on
CPU 2 etc...).

By default fibtest spawns one fast thread on CPU 0 and a number of slow
threads equal to the number of CPUs minus the number of fast threads.

## Running fibtest
```
$ ./runfibtest 1; ./runfibtest
```

`runfibtest` optionally takes an argument for the total number of threads to spawn. With no argument
it will spawn one fast thread and as many slow threads as are equal to one less than the total number of
CPUs.

It returns the number of iterations of the Fibonacci sequence it was able to accomplish as well as how
long it was throttled and the corresponding CPU usage.

## Code of Conduct
This project is governed by the [Contributor Covenant v 1.4.1](CODE_OF_CONDUCT.md)

## License

[Apache License Version 2.0](https://github.com/indeedeng/throttletest/blob/master/LICENSE)
