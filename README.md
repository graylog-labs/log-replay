# log-replay
Replay script for sending log files into Graylog

# Usage

```
log_sender.py [-h] [-s SERVER] [-p PORT] [-u] [-d [0-1000]] [-l LINES] [-c] [-r] [-w] [-m MESSAGE | -f FILE]

A program for sending arbitrary syslog messages to a Graylog server using TCP. This can be used to test any Input built on Raw or Syslog TCP such as Palo Alto.

options:
  -h, --help            show this help message and exit
  -s SERVER, --server SERVER
                        The syslog server (defaults to "localhost")
  -p PORT, --port PORT  The syslog port (defaults to 514)
  -u, --udp             Send message using UDP rather than TCP
  -d [0-1000], --delay [0-1000]
                        Add a delay in milliseconds [0-1000] after sending each line of a file
  -l LINES, --lines LINES
                        Limit number of lines to transmit (0 = no limit)
  -c, --csv             When sending CSV file this option will skip the first line
  -r, --raw             Send messages without adding the syslog formatting. Intended for sending log lines to raw TCP/UDP inputs.
  -w, --wrap            When enabled, will restart file from beginning until -l/--lines count is met (default: 1000 lines)
  -m MESSAGE, --message MESSAGE
                        The message to be sent (may need to be surrounded by 'single quotes' if it contains spaces)
  -f FILE, --file FILE  A newline-delimited file of messages to be sent

You must provide either a message or an input file. Note that when using -w/--wrap that -l/--lines cannot be set to 0, and the line count will be set to 1000 by
default.
```
