---
layout: page
title: How To Release
nav_order: 10
parent: Developers
grand_parent: Documentations
permalink: /docs/developers/how-to-release/
---
# How to Release

This section outlines the steps for releasing Apache Gluten (incubating) according to the Apache release guidelines.
All projects under the Apache umbrella must adhere to the [Apache Release Policy](https://www.apache.org/legal/release-policy.html). This guide is designed to assist you in comprehending the policy and navigating the process of releasing projects at Apache.


## Release Process

1. Prepare the release artifacts.

2. Upload the release artifacts to the SVN repository.

3. Verify the release artifacts.

4. Initiate a release vote.

5. Announce the results and the release.


### Prepare the release artifacts.

1. Create a branch from the target git repository.

2. Tag a RC and draft the release notes.

3. Build and Sign the release artifacts (including source archives, binaries, ...etc).

4. Generate checksums for the artifacts.


#### How to Sign the release artifacts.

1. Create a GPG key

2. Add the GPG key to the KEYS file

3. Sign the release artifacts with the GPG key.

```bash
# create a GPG key, after executing this command, select the first one RSA 和 RSA
$ gpg --full-generate-key

# list the GPG keys
$ gpg  --keyid-format SHORT --list-keys

# upload the GPG key to the key server, xxx is the GPG key id
# eg: pub rsa4096/4C21E346 2024-05-06 [SC], 4C21E346 is the GPG key id;
$ gpg --keyserver keyserver.ubuntu.com --send-key xxx

# append the GPG key to the KEYS file the svn repository
# [IMPORTANT] Don't replace the KEYS file, just append the GPG key to the KEYS file. 
$ svn co https://dist.apache.org/repos/dist/release/incubator/answer/
$ (gpg --list-sigs xxx@apache.org && gpg --export --armor xxx@apache.org) >> KEYS 
$ svn ci -m "add gpg key" 

# sign the release artifacts, xxxx is xxx@apache.org
$ for i in *.tar.gz; do echo $i; gpg --local-user xxxx --armor --output $i.asc --detach-sig $i ; done
```


#### How to Generate checksums for the release artifacts.

```bash
# create the checksums
$ for i in *.tar.gz; do echo $i; sha512sum  $i > $i.sha512 ; done
```


### Upload the release artifacts to the SVN repository.

1. Create a project directory in the SVN repository (1st time only).
`https://dist.apache.org/repos/dist/dev/incubator/gluten/`

2. Create a directory for the release artifacts in the SVN repository.
`https://dist.apache.org/repos/dist/dev/incubator/gluten/{release-version}`
release-version format: apache-gluten-#.#.#-rc#

3. Upload the release artifacts to the SVN repository.
```bash
$ svn co https://dist.apache.org/repos/dist/dev/incubator/gluten/
$ cp /path/to/release/artifacts/* ./{release-version}/
$ svn add ./{release-version}/*
$ svn commit -m "add Apache Answer release artifacts for {release-version}"
```

4. After the upload, please visit the link `https://dist.apache.org/repos/dist/dev/incubator/gluten/{release-version}` to verify if the file upload is successful or not.
The upload release artifacts should be include
```bash
* apache-gluten-#.#.#-incubating-src.tar.gz
* apache-gluten-#.#.#-incubating-src.tar.gz.asc
* apache-gluten-#.#.#-incubating-src.tar.gz.sha512
```


### Verify the release artifacts.

Please follow below steps to verify the release artifacts.

1. Check if the Download links are valid.

2. Check if the checksums and GPG signatures are valid.

3. Check if the release artifacts name is qualified and match with the current release.

4. Check if LICENSE and NOTICE files are correct.

5. Check if the License Headers are included in all files if necessary.

6. No unlicensed compiled archives bundled in source archive.


#### How to Verify the Signatures

Please follow below steps to verify the signatures.

```bash
# download KEYS
$ curl https://dist.apache.org/repos/dist/release/incubator/gluten/KEYS > KEYS

# import KEYS and trust the key, please replace the email address with the one you want to trust.
$ gpg --import KEYS
$ gpg --edit-key xxx@apache.org
gpg> trust
gpg> 5
gpg> y
gpg> quit

# enter the directory where the release artifacts are located
$ cd /path/to/release/artifacts

# verify the signature
$ for i in *.tar.gz; do echo $i; gpg --verify $i.asc $i ; done

# if you see 'Good signature' in the output, it means the signature is valid.
```


#### How to Verify the checksums

Please follow below steps to verify the checksums
```bash
# verify the checksums
$ for i in *.tar.gz; do echo $i; sha512sum --check  $i.sha512; done
```


### Initiate a release vote.

1. Email a vote request to dev@gluten.apache.org, requiring at least 3 PPMC +1s.

2. Allow 72 hours or until enough votes are collected.

3. Share the vote outcome on the dev list.

4. If successful, request a vote on general@incubator.apache.org, needing 3 PMC +1s.

5. Wait 72 hours or for sufficient votes.

6. Announce the results on the general list.

Vote Email Template
```
[VOTE] Release Apache Gluten (Incubating) {release-version}

Hello,

    This is a call for vote to release Apache Gluten (Incubating) version {release-version}.

    The vote thread:
        https://lists.apache.org/thread/{id}

    Vote Result:
        https://lists.apache.org/thread/{id}

    The release candidates:
        https://dist.apache.org/repos/dist/dev/incubator/gluten/{release-version}/
    
    Release notes:
        https://github.com/apache/incubator-gluten/releases/tag/{release-version}

    Git tag for the release:
        https://github.com/apache/incubator-gluten/releases/tag/{release-version}
    
    Git commit id for the release:
        https://github.com/apache/incubator-gluten/commit/{id}

    Keys to verify the Release Candidate:
        https://downloads.apache.org/incubator/gluten/KEYS
        
    The vote will be open for at least 72 hours or until the necessary number of votes are reached.

    Please vote accordingly:

    [ ] +1 approve
    [ ] +0 no opinion
    [ ] -1 disapprove with the reason

    Checklist for reference:

    [ ] Download links are valid.
    [ ] Checksums and PGP signatures are valid.
    [ ] Source code distributions have correct names matching the current release.
    [ ] LICENSE and NOTICE files are correct for each Apache Answer repo.
    [ ] All files have license headers if necessary.
    [ ] No unlicensed compiled archives bundled in source archive.

    To compile from the source, please refer to:
    
    https://github.com/apache/incubator-gluten#building-from-source

Thanks,
<YOUR NAME>
```


### Announce the results and the release.


Announce Email Template
```
Hello everyone,

The Apache Gluten (Incubating) {release-version} has been released!

Apache Gluten is a Q&A platform software for teams at any scale.
Whether it's a community forum, help center, or knowledge management platform, you can always count on Apache Answer.

Download Links: https://downloads.apache.org/incubator/gluten/

Release Notes: https://github.com/apache/incubator-gluten/releases/tag/{release-version}

Website: https://gluten.apache.org/

Resources:
- Issue: https://github.com/apache/incubator-gluten/issues
- Mailing list: dev@gluten.apache.org

Thanks,
<YOUR NAME>

```
