# Overview #

DAVTest tests WebDAV enabled servers by uploading test executable files, and then (optionally) uploading files which allow for command execution or other actions directly on the target.

  * Automatically send exploit files if code executes
  * Automatic randomization of directory to help hide files using MKCOL
  * Send text files and try MOVE to executable name
  * Basic and Digest authorization
  * Automatic clean-up of uploaded files
  * Send an arbitrary file