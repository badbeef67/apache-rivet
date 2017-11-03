# Alpine Linux image running Apache Rivet

Base image: Alpine Linux 3.6
Packages: apache2, apache2-dev, tcl-dev, expect
Complied from source: rivet-2.3.4

## Post-Config
Apache must be configured with the following to load the rivet module. Consider loading a custom httpd.conf file when executing the docker run command, or ADD/COPY to this Dockerfile.

\#/etc/apache2/httpd.conf

\# Dynamic Shared Object (DSO) Support
LoadModule rivet_module	/usr/lib/apache2/mod_rivet.so

\# AddType allows you to add to or override the MIME configuration
\# file specified in TypesConfig for specific file types.
AddType application/x-httpd-rivet .rvt
AddType application/x-rivet-tcl .tcl
AddType 'application/x-httpd-rivet;charset=utf-8' rvt

\# DirectoryIndex: sets the file that Apache will serve if a directory
\# is requested.
DirectoryIndex index.html index.htm index.shtml index.cgi index.tcl index.rvt

## Usage
`docker run -d -p 4000:80 badbeef67/apache-rivet`