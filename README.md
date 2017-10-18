# misc-tools

## sync-secure-s3
- syncs any tree with an S3 bucket
- encrypts files before upload using a key that is only held locally in the OS/X keychain

## refresh-repos
- syncs all repos under one directory with their origin/master
- requires the var REPO_HOME to be set, pointing to the top-level directory holding the repos
