#Daemonator (0.4.1.1) Formerly Daemon-Python
Lightweight and no-nonsense POSIX daemon library. Extensible, complete with process forking and [PID][4] management. 

Inspired by [Sander Marechal][2].

##License
MIT/X11 - See [LICENSE][1]

##Getting Started

**Installation**

		# git clone https://github.com/flaviocpontes/daemonator.git
		# cd daemonator/
		# python setup.py install

1. **Instantiation**

		import daemon
		class MyDaemon(daemon.Daemon):
		"""Subclass Daemonator."""
		...
			def run(self):
			"""Define what to daemonize by implementing the run() method."""
			...

2. **Implementing control**

	Finally, we want to be able to control our daemon.
	
		...
		if __name__ == "__main__":
		    daemon = MyDaemon('/tmp/mydaemon.pid') #Define a pidfile location (typically located in /tmp or /var/run)
		    if len(sys.argv) == 2:
		        if 'start' == sys.argv[1]:
		            daemon.start()
		        elif 'stop' == sys.argv[1]:
		            daemon.stop()
		        elif 'restart' == sys.argv[1]:
		            daemon.restart()
		        elif 'status' == sys.argv[1]:
		            daemon.status()
		        else:
		            sys.stdout.write("Unknown command\n")
		            sys.exit(2)
		        sys.exit(0)
		    else:
		        sys.stdout.write("Usage: %s start|stop|restart|status\n" % sys.argv[0])
		        sys.exit(2)

  [1]: https://github.com/flaviocpontes/daemonator/blob/master/LICENSE
  [2]: http://www.jejik.com/articles/2007/02/a_simple_unix_linux_daemon_in_python/
  [3]: https://github.com/stackd/daemon-py/blob/master/src/test.py
  [4]: http://en.wikipedia.org/wiki/Process_identifier
