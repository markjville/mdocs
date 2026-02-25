# Batch Delete Files

Find files and delete

You want to remove multiple files such as ‘*.jpg’ or ‘*.sh’ with one command find, try:

`find . -name "FILE-TO-FIND" -exec rm -rf {} \;`

Or for specifying directory:

`find /dir/to/search/ -type f -name "FILE-TO-FIND-Regex" -exec rm -f {} \;`

Or use the “-delete” option if terminal supports it.

`find /dir/to/search/ -type f -name "FILES-TO-FIND" -delete`
