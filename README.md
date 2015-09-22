# NAME

gearctl - Gearman daemon controller, with graceful shutdown

# SYNOPSIS

    gearctl [options]

    Options:

         --host <arg>  the server's host (default localhost)
         --port <arg>  the server's port (default 4730)
         --workers     a list all workers
         --status      a list of functions
         --shutdown    shutdown the server without draining the queue
         --graceful    drain queue before shutting down the server
         --version     reports the server version
     -h, --help        brief help message
     -m, --man         full documentation

# OPTIONS

- --host &lt;arg>

    Default: localhost

    Connect to the server on this host.

- --port &lt;arg>

    Default: 4730

    Connect to the server on this port.

- --workers

    This sends back a list of all workers, their file descriptors, their IPs, their
    IDs, and a list of registered functions they can perform. The list is
    terminated with a line containing a single '.' (period). The format is:

        FD IP-ADDRESS CLIENT-ID : FUNCTION ...

- --status

    This sends back a list of all registered functions.  Next to each function is
    the number of jobs in the queue, the number of running jobs, and the number of
    capable workers. The columns are tab separated, and the list is terminated with
    a line containing a single '.' (period). The format is:

        FUNCTION\tTOTAL\tRUNNING\tAVAILABLE_WORKERS

- --shutdown

    Shutdown the server immediately.  Any jobs in non-durable queues will be lost.

- --graceful

    Shutdown the server after preventing further jobs from being added to the
    queue, and allowing remaining jobs to complete.  This can be useful if you want
    to fail jobs over to another server, but don't want to lose jobs that are
    already queued.

- --version

    Report the server's version.

- -h, --help

    Print a brief help message, then exit.

- -m, --man

    Print the manual page, and then exit.

# DESCRIPTION

`gearctl` is an alternative to `gearadmin` - one which provides the option to
gracefully shutdown a gearman server.
