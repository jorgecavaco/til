# Java tricks and hacks

* jps used to obtain java PID  
* jstat -gc [insert-pid-here] to find statistics of the behaviour of the garbage collected heap.
* jstat -gccapacity [insert-pid-here] will present information about memory pool generation and space capabilities.
* jstat -gcutil [insert-pid-here] will present the utilisation of each generation as a percentage of its capacity (Useful to get an at a glance view of usage).
