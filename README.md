# misc-tools


# Configuration
- config values are read from in environment variables. See list below.

# Tools here
## sync-secure-s3
- syncs any tree with an S3 bucket
- encrypts files before upload using a key that is only held locally in the OS/X keychain
- requires the vars S3_SYNC_SECURE_SOURCE_PATH_DESTS, S3_SYNC_SECURE_ENCRYPTION_KEY_LABEL_IN_KEYCHAIN
with the name of the encrypt/decrypt secret on the OS/X keychain

## refresh-repos
- syncs all repos under one directory with their origin/master
- requires the vars REPO_HOME, REPO_REMOTE, REPO_REMOTE_BRANCH

## aws-ssh
- ssh to an AWS host by its instance-id, or its full or partial name: tag
- supports ssh to a private IP through a proxy, or directly to a public IP
- requires the var AWS_SSH_TUNNEL_HOST if using a proxy

# Configuration environment variables
- set these in your bash config file (~/.bash_profile on OS/X or whatever)

### Top-level directory/directories where the files to be sync'd are
Format is: "source path,s3://bucket[/optional/path/in/bucket]"
- First example below syncs Photos on a Mac to MYBUCKET/photoslibrary
- Second example below syncs a sparsebundle virtual volume to MYBUCKET/Private.sparsebundle

```
export S3_SYNC_SECURE_SOURCE_PATH_DESTS=(
"${HOME}/Pictures/Photos Library.photoslibrary,s3://MYBUCKET/photoslibrary"
"${HOME}/Private.sparsebundle,s3://MYBUCKET/Private.sparsebundle"
)
```

### Encryption key's label in the OS/X Keychain. Script will look it up.
```
export S3_SYNC_SECURE_ENCRYPTION_KEY_LABEL_IN_KEYCHAIN="s3photospassword"
```

### The directory holding all the repos for refresh-repos and other repo tools
```
export REPO_HOME=/Users/MYNAME/workspace
```

### Name of the git repo remote, usually "origin", sometimes "upstream" or whatever
```
export REPO_REMOTE=origin
```

### Name of the master branch on the remote repo, usually "master"
```
export REPO_REMOTE_BRANCH=master
```

### IP or hostname of host to tunnel through with aws-ssh (optional)
- If empty, aws-ssh will return public IP of host and connect directly.
- If set, aws-ssh will connect to private IP of host via this tunnel host.

```
export AWS_SSH_TUNNEL_HOST=
```
