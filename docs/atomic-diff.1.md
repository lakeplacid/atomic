% ATOMIC(1) Atomic Man Pages
% Brent Baude
% November 2015
# NAME
atomic-diff - show the differences between two images|containers RPMs
# SYNOPSIS
**atomic diff**
[**-h**|**--help**]
[**--json**]
[**--names-only**]
[**-n**][**--no-files**]
[**-r**][**--rpms**]
[**-v**][**--verbose**]
image|container image|container ...]

# DESCRIPTION
**atomic diff** will compare the files found in two different images or containers
and output to stdout or as JSON. By default,  the comparison is done on the file level
but there are switches for comparing RPMs and metadata as well.

# OPTIONS
**-h** **--help**
  Print usage statement.

**--json**
  Output in the form of JSON.

**-k** **--keywords**
  Use the following keywords for comparison of files.  You must select at least one but multiple can
  be used as well. Keywords that are used for this option are exclusive, which means that any only those
  keywords will be used.
  
  Keywords currently defined are: **all**, **link**, **nlink**, **mode**, **type**, **time**, **uid**, **gid**, **size**, **sha256digest**

**-m** **--metadata**
  Show the differences in the metadata for the two images or containers.
  
**-n** **--no-files**
  Do not perform a file based diff between the two images or containers.  Often used
  when performing an RPM-based diff to restrict output.

**--names-only**
  When performing the diff, only compare package names and not their versions.

**-r** **--rpms**
  Show the where the two docker objects have different RPMs.

**-v** **--verbose**
  Be verbose in showing the differences in RPMs.  The default will only show the differences in RPMs, whereas
  with **verbose** it will show all the RPMS in each object.
  


# EXAMPLES
Compare images the files in 'foo1' and 'foo2'.

    atomic diff foo1 foo2

Compare the files in images 'foo1' and 'foo2' and output in JSON.

    atomic diff --json foo1 foo2

Compare only the RPMs in images 'foo1' and 'foo2'

    atomic diff -r -n foo1 foo2

Compare the files and RPMs (without versions) in images 'foo1' and 'foo2' and output as json

    atomic diff -r --json foo1 foo2
    
Compare only the metadata between images 'foo1' and 'foo2'

    atomic diff -m foo1 foo2
    
Compare files by 'sha256digests' and 'time' between images 'foo1' and 'foo2'

    atomic diff foo1 foo2 --keywords sha256digest time

# HISTORY
Updated by Brent Baude (bbaude at redhat dot com) Nov 2016
Updated by Brent Baude (bbaude at redhat dot com) May 2016
Initial revision by Brent Baude (bbaude at redhat dot com) November 2015
