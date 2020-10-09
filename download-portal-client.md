# Downloading using the Portal Client

Python-based client for downloading data files hosted by the an instance of
the portal software developed by the GDC and further modified by the
Institute for Genome Sciences (IGS). There are several portals running on the
internet to support various research efforts. Notably, the HMBR Archive uses the portal
to enable data exploration and download. The client accepts a *manifest file*
as an input. This file contains URLs to the files to be downloaded. Manifest
files can be generated using the shopping cart functionality of the portal's
query interface.

## Installation
The IGS portal client can be downloaded from [here](https://github.com/IGS/portal_client).

## Usage

When properly installed, portal_client will be available for direct invocation
from the command line. Running `which portal_client` should yield a result, and
will show precisely where the script is installed. General usage is available
by simply using the well-known `--help`, or `-h`.

```bash
portal_client --help
```

This will output all the options that portal_client supports as well as a
very brief explanation of what each option means and how it modifies the
execution.

## 1. Basic invocation

The following command is the most basic way of invoking the client. Simply by
specifying the path to a downloaded manifest file with the `-m`, or `--manifest`
option.

```bash
portal_client --manifest /path/to/my/manifest.tsv
```

Since manifests can list multiple URLs for an entry (a file can be obtained
from multiple sources), when using portal_client in this manner, it uses a
default set of protocols to download the data in the manifest. These
protocols are, in priority order: HTTP, FTP, and S3. HTTP uses the http
protocol for downloads of URLS starting with `http://`, while FTP uses the File
Transfer Protocol for `ftp://` links, and S3 will fetch data from Amazon AWS
Simple Storage Service (S3) buckets. If a download cannot be performed for
a file with HTTP, and the file is available via S3 and FTP, by default, the
client will next attempt an FTP transfer, followed finally by S3...


## 2. Altering the target directory

By default, portal_client will download data to the same directory (the
"working director"), that the user invoked portal_client from. To alter the
location of where the data should be deposited, one must use the
`--destination` option:

first be generated. Documentation for how that is accomplished is available
from Google and is beyond the scope of this guide, but it is used to
authorize the portal_client to access data in a Google storage bucket.
Additionally, the ID of a valid Google project must also be specified with
the `--google-project-id` option. A full example is below:

```bash
portal_client --manifest /path/to/my/manifest.tsv \
  --destination /path/to/my/destination/directory
```

## 3. Overriding the default endpoint-priority

Sometimes, it may be advantageous to override the default endpoints, and their
priorities, that the portal_client will consider when downloading data. This is
accomplished with the `--endpoint-priority` option.

```bash
portal_client --manifest /path/to/my/manifest.tsv --endpoint-priority S3
```

In the above example, portal_client will NOT consider or attempt to download
data from HTTP or FTP urls. It will only use `s3://` urls. Any URLs that do NOT
use the `s3://` protocol will be skipped.

## 4. Disabling checksum validation

The portal_client usually verifies downloads after they happen by performing
and MD5 checksum on the downloaded data, and comparing it to the checksums
listed in the manifest file. However, if there is a mismatch, portal_client
will consider the download to be corrupted, or failed, and will exit out
with an error message. For very manifests that describe extremely large
datasets, the checksumming operation can be very costly, or time consuming.
To disable the checksum validation, simply pass an extra `--disable-validation`
Example:

```bash
portal_client --disable-validation --manifest /path/to/my/manifest.tsv
```

## 5. Debug mode

Users can see verbose additional information when executing portal_client by
passing the `--debug` option. This will typically result in a large amount of
output and can be used to trace where problems may be occuring. This output is
frequently used by developers when troubleshooting.