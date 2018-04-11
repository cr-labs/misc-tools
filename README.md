# misc-tools


# Configuration
- config vars are in a separate path from the tools, "../misc-tools-config"
- the adjacent repo here, `misc-tools-config-example` shows example config
for all variables required by tools here

# Tools here
## sync-secure-s3
- syncs any tree with an S3 bucket
- encrypts files before upload using a key that is only held locally in the OS/X keychain
- requires the vars S3_SYNC_SECURE_SOURCE_PATH_DESTS, S3_SYNC_SECURE_ENCRYPTION_KEY_LABEL_IN_KEYCHAIN
with the name of the encrypt/decrypt secret on the OS/X keychain

## refresh-repos
- syncs all repos under one directory with their origin/master
- requires the vars REPO_HOME, REPO_REMOTE, REPO_REMOTE_BRANCH
