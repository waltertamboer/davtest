# Tests #

Tests are used to determine if the server can execute a certain type of code. Each test may have a corresponding backdoor file, but backdoor files **must** have a corresponding test to determine if that file type can execute on the server. It is recommended a simple/basic operation for each language is used--by default, the supplied tests use mathematical calculations where possible.

Test files are located in the 'test/' directory. Files must be named according to
the type of program file they will become on the server. For example, a file named 'php.txt' will be put to the server with a .php extension.

Each file must have two lines, 'content' and 'execmatch'--the body put to the server and regex to  match to see if it executed. For example, the php.txt contents are:
> `content=<?php print 7.8 * 6.4;?>`

> `execmatch=49.92`

Additionally, the token `$$FILENAME$$` will be replaced (with the PUT file's name) in the content before it sent to the server. Embedded newlines (\n) will be converted to actual newlines (to accommodate PERL).

# Backdoors #

Backdoor files are located in the 'backdoors/' directory. They must have the match extension for the type they will be uploaded for. For example, a PHP backdoor must have a '.php' extension.

A backdoor file can contain any code you desire, and multiple backdoor files may be used for a file type. If multiple files exist for a type, each will be uploaded when appropriate.

A backdoor type (e.g., PHP) **must** have a corresponding type in the 'tests/' directory, otherwise it will never be tested/uploaded.