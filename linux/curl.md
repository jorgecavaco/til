# cURL

A command line tool and library for transferring data with URL syntax, supporting HTTP, HTTPS, FTP, FTPS, GOPHER, TFTP, SCP, SFTP, SMB, TELNET, DICT, LDAP, LDAPS, FILE, IMAP, SMTP, POP3, RTSP and RTMP.

## Usage

For sending data with POST and PUT requests, these are common curl options:
* request type
  * -X POST
  * -X PUT
* content type header
  * ```-H "Content-Type: application/x-www-form-urlencoded"```
* data
  * form urlencoded:
    * ```-d "param1=value1&param2=value2" or -d @data.txt```
  * json:
    * ```-d '{"key1":"value1", "key2":"value2"}' or -d @data.json```


## Common Options
    -#, --progress-bar Make curl display a simple progress bar instead of the more informational standard meter.

    -b, --cookie <name=data> Supply cookie with request. If no =, then specifies the cookie file to use (see -c).

    -c, --cookie-jar <file name> File to save response cookies to.

    -d, --data <data> Send specified data in POST request. Details provided below.

    -f, --fail Fail silently (don't output HTML error form if returned).

    -F, --form <name=content> Submit form data (will add enctype=”multipart/form-data” to the request).

    -H, --header <header> Headers to supply with request.

    -i, --include Include HTTP headers in the output.

    -I, --head Fetch headers only.

    -k, --insecure Allow insecure connections to succeed.

    -L, --location Follow redirects.

    -o, --output <file> Write output to . Can use --create-dirs in conjunction with this to create any directories specified in the -o path.

    -O, --remote-name Write output to file named like the remote file (only writes to current directory).

    -s, --silent Silent (quiet) mode. Use with -S to force it to show errors.

    -v, --verbose Provide more information (useful for debugging).

    -w, --write-out <format> Make curl display information on stdout after a completed transfer. See man page for more details on available variables. Convenient way to force curl to append a newline to output: -w "\n" (can add to ~/.curlrc).

    -X, --request The request method to use.

### Examples
* POST application/x-www-form-urlencoded (application/x-www-form-urlencoded is the default)
  - curl -d "param1=value1&param2=value2" -X POST http://localhost
  - explicit:
    - curl -d "param1=value1&param2=value2" -H "Content-Type: application/x-www-form-urlencoded" -X POST http://localhost
  - with a data file
    - curl -d "@data.txt" -X POST http://localhost
  - POST application/json
    - curl -d '{"key1":"value1", "key2":"value2"}' -H "Content-Type: application/json" -X POST http://localhost
  - with a data file
    - curl -d "@data.json" -X POST http://localhost
  - upload files
    - curl -F ‘data=@path/to/local/file’ http://localhost/upload
  - upload multiple files
    - curl -F 'fileX=@/path/to/fileX' -F 'fileY=@/path/to/fileY' ... http://localhost/upload
  - hide output
    - curl --silent --output /dev/null http://localhost
    - curl --write-out '%{http_code}' --silent --output /dev/null http://localhost


## Advance usage

Display total time, in seconds, that the full operation lasted:
`curl -o /dev/null -s -w 'Total: %{time_total}\n'  https://localhost`

cURL supports formatted output for the details of the request (see the cURL manpage for details, under -w, –write-out <format>).

Create a new file, curl-format, and paste in:

  time_namelookup:  %{time_namelookup}\n
  time_connect:  %{time_connect}\n
  time_appconnect:  %{time_appconnect}\n
  time_pretransfer:  %{time_pretransfer}\n
  time_redirect:  %{time_redirect}\n
  time_starttransfer:  %{time_starttransfer}\n
  time_total:  %{time_total}\n

Make a request:
```curl -w "@curl-format" -o /dev/null -s "http://localhost/"```

What this does:
-w "@curl-format" tells cURL to use our format file
-o /dev/null redirects the output of the request to /dev/null
-s tells cURL not to show a progress meter
"http://localhost/" is the URL we are requesting. Use quotes particularly if your URL has "&" query string parameters

And here is what you get back:

time_namelookup:  0.001
time_connect:  0.037
time_appconnect:  0.000
time_pretransfer:  0.037
time_redirect:  0.000
time_starttransfer:  0.092
time_total:  0.164


## Resources
* https://blog.josephscott.org/2011/10/14/timing-details-with-curl/
* https://github.com/curl/curl
* https://curl.haxx.se/docs/manpage.html
