# Requirements #
  * PERL 5.x
  * HTTP::DAV

# Option List #
|auth+ |	Authorization (user:password)|
|:-----|:-----------------------------|
|cleanup|	delete everything uploaded when done|
|directory+|	postfix portion of directory to create|
|debug+|	DAV debug level 1-3 (2 & 3 log req/resp to /tmp/perldav\_debug.txt)|
|move	 |	PUT text files then MOVE to executable|
|nocreate |	don't create a directory     |
|quiet	 |	only print out summary       |
|rand+ | 	use this instead of a random string for filenames|
|sendbd+|	send backdoors:              |
|      |			auto - for any succeeded test|
|      |			ext - extension matching file name(s) in backdoors/ dir|
|uploadfile+|	upload this file (requires -uploadloc)|
|uploadloc+|	upload file to this location/name (requires -uploadfile)|
|url+$	|	url of DAV location          |
|+ Option requires a value|
|$ Option is required|


# Options Explained #
  * **auth** (requires value): Send this username/password for Basic or Digest authorization.
  * **cleanup**: Delete all files successfully put to the server before exiting.
  * **directory** (requires value): Static portion of directory name to use when running MKCOL (instead of fully random name)
  * **debug** (requires value): Turn on HTTP:DAV debugging, which logs to /tmp/perldav\_debug.txt).
  * **move**: Attempt to put files with a txt extension and then issue MOVE to change it to an executable file name.
  * **nocreate**: Don't create a new directory.
  * **quiet**: Only print out summary before exiting.
  * **rand** (requires value): Use this instead of a random string for filenames.
  * **sendbd** (requires value): Send backdoor files. "auto" sends an appropriate backdoor for any executable that worked, or "ext" (e.g., "php") to match files in the 'backdoors/' directory. Do not include the leading dot for the extension.
  * **uploadfile** (requires value): Upload this file (requires -uploadloc).
  * **uploadloc** (requires value): Upload -uploadfile to this name/location (requires -uploadfile).
  * **url** (requires value, required): This is the URL to the DAV location.


# Examples #
Test file uploads at this location:
  * `davtest.pl -url http://localhost/davdir`

Test file uploads at this location and send backdoors for any types which execute successfully:
  * `davtest.pl -url http://localhost/davdir -sendbd auto`

Upload a file using authentication, send the perl\_cmd.pl backdoor and call it perl.pl on the server:
  * `davtest.pl -url http://localhost/davdir -auth user:pass -uploadfile backdoors/perl_cmd.pl -uploadloc perl.pl`