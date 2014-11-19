HEADCHECK: a HTTP headers requester for monitoring websites
===========================================================

Ben Carpenter  
2011-2014

	Usage: headcheck [options] [-f file|url[ url[ ...]]|-]

HEADCHECK runs a header check on the URL hosted at the address
or addresses passed in as a file, as space separated arguments,
or as a space separated list over standard input.  Various items
of data and durations are recorded.  Included is a log file that
records the last check results and optionally a database that
logs the results from every run.

For each check the following information is presented in comma
separated format:

    url                 URL requested
    datetime            Date and time of request
    ip                  IP address found from host lookup
    http_code           HTTP code from headers
    redirect_url        Redirect location from a HTTP 3xx code,
                        if present
    time_total          Total time taken for the header request
                        to complete
    time_namelookup     Time from start until name resolving
                        completed
    time_connect        Time from start until TCP connection to
                        the host completed
    time_pretransfer    Time from start until file transfer is
                        about to begin
    time_starttransfer  Time from start until first byte was
                        about to be transferred

This information is written to the console and stored in the log
as one line per URL. If the -c option is used, the output to
the console is suppressed. The log file has a backup denoted by
a ~ extension; the difference between the current and last log
at any given time is the last check performed.

Options
-------

    -a email  Send an alert to this email address 
              when a change in status code or IP 
              address is detected
    -c        Run with cron compatibility
              (suppress normal output)
    -d        Use database
    -D file   Use database file, implies -d
              (default headcheck.db)
    -f file   Select URLs at random from file
    -h        Show this message
    -i ip,ip  Send alerts when some change happens 
              and the IP address appears in this 
              comma-separated list
    -l file   Log file to use
              (default headcheck.log)
    -n N      With -f, select N URLs from file
              (default 10)
    -t N      Timeout each check at N seconds
              (default 10)
    -u agent  User agent string to use for curl
    -         Read URL list from standard input

Dependencies
------------

cURL 7.29 or later for requests, optionally SQLite 3 for database
storage features
