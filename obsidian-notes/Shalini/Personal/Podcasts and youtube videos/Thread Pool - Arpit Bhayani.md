Say we have a web server, and whenever a client connects to it we fork a new thread to handle the request. So, if there are 'n' concurrent request, we would have 'n' threads handling them.

**This looks awesome, so what is the problem?**
What happens when 'n' shoots up?
	- we would have large threads running
	- consuming resources
	- overwhelming the hardware
	- it hangs and crashes the machine
Thus we cannot have threads spinnign up every now and then.
We need to limit the maximum number of threads we create.

This is exactly what "**Thread pools**" solves.

Real world use cases - 
	- Web servers to handle multiple clients simultaneously.
	- Async processing of messages from broker.


**What is Thread Pool ?**
Thread pool is a 'collection' of worker threads that are used to execute tasks simultaneously.
Whenever we want a thread we pick one from this pool ans delegate the task to it. Once the task is complete we add the thread back to the thread pool.

eg. - 
When a web server spins up, it creates a thread pool of 'n' when a client connects to the web server, we pick one thread to handle the request . once the response is generated and sent, the thread is added back to the pool.

**Stable performance**
The size of the pool is limited (bounded) and hence, when your application (web server) needs a thread but it is empty the application waits until some thread is done and adds backs to the pool.

Hence threads are copped, so hardware never overwhelms!!

**What should be the size of a thread pool?**
It is difficult to 'tune' a thread pool.
	Too small - You are not utilizing your hardware
			- tasks queues up
			- slow progress
	Too huge - Your hardware overwhelms

**Tuning the thread pool**
There is no golden rule to tune the thread pool and it depends totally on the application.

Here are few factors to consider while deciding the size of the pool.
- Number of processors available
- Characteristics of tasks being executed.
