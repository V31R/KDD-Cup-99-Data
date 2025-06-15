# KDD Cup 99 Data

This dataset is a cleaned and reformatted version of the original [KDD Cup 1999](http://kdd.ics.uci.edu/databases/kddcup99/kddcup99.html) dataset.
**License**: CC BY-NC-SA 4.0 — see full terms at the bottom of this page.

## Usage

- **Multiclass classification** (40-class and 5-class versions).
- **Binary classification** (attack and normal).
- **Unsupervised anomaly detection** (using unlabeled data).

## Original task description

**Task**: Build a network intrusion detector that distinguishes between "normal" and "attack" connections.
**Features**: 41 attributes capturing characteristics of network connections, such as duration, protocol, number of failed logins, etc.
**Target (label)**: One of 40 connection types, including normal traffic and various attack categories (DoS, Probe, R2L, U2R).

More info: [KDD Cup 1999 Task Description](https://kdd.ics.uci.edu/databases/kddcup99/task.html).

## Dataset Modifications

This version of the dataset includes the following modifications:

- Converted the original 40-class label into:
  - **5-class version** by grouping connection types into: `dos`, `probe`, `r2l`, `u2r`, `normal`.
  - **binary version** by labeling all attacks as `attack` and keeping `normal` as-is.
- Added feature `connection_type` as target label for classification.
- For clean versions, the `num_outbound_cmds` feature has been removed.

## Features description

> ⚠️ **Important note on label distribution across sets**
>
> There is a significant mismatch between the training/full and test sets in the full 40-class version of the dataset:
>
> - The **training/full sets** contains 22 attack types + `normal`, totaling **23 labels**.
> - The **test set** contains 37 attack types + `normal`, totaling **38 labels**.
> - The **combined set of labels** contains **40 labels**.
>
> **2 attack types** appear **only in the train and full sets**: `warezclient`,`spy`.
>
> **17 attack types** appear **only in the test set**: `xlock`, `ps`, `xterm`, `processtable`, `snmpguess`, `sqlattack`, `httptunnel`, `mscan`, `worm`, `apache2`, `snmpgetattack`, `saint`, `sendmail`, `mailbomb`, `xsnoop`, `udpstorm`, `named`.

### Feature table

| feature | type | description |
| :------ | :------: | :------ |
| duration  |  integer | length (number of seconds) of the connection   |
| protocol_type | categorical    | type of the protocol, e.g. tcp, udp, etc.    |
| service   | categorical  | network service on the destination, e.g., http, telnet, etc.    |
| flag  | categorical  | normal or error status of the connection   |
| src_byte  |  integer  | number of data bytes from source to destination   |
| dst_bytes |  integer  | number of data bytes from destination to source   |
| land  |  integer  | 1 if connection is from/to the same host/port; 0 otherwise    |
| wrong_fragment    |  integer  | number of ``wrong'' fragments   |
| urgent    |  integer  | number of urgent packets  |
| hot   |  integer  | number of ``hot'' indicators   |
| num_failed_logins |  integer  | number of failed login attempts |
| logged_in |  integer  | 1 if successfully logged in; 0 otherwise  |
| num_compromised |  integer  | number of ``compromised'' condition |
| root_shell    |  integer  | 1 if root shell is obtained; 0 otherwise  |
| su_attempted  |  integer  | 1 if ``su root'' command attempted; 0 otherwise   |
| num_root  |  integer  | number of ``root'' accesses   |
| num_file_creations |  integer  | number of file creation operations   |
| num_shells    |  integer  | number of shell prompts   |
| num_access_files  |  integer  | number of operations on access control files    |
| num_outbound_cmds |  integer  | number of outbound commands in an ftp session |
| is_host_login |  integer  | 1 if the login belongs to the ``host'' list; 0 otherwise   |
| is_guest_login    |  integer  | 1 if the login is a ``guest'' login; 0 otherwise   |
| count |  integer  | number of connections to the same host as the current connection in the past two seconds  |
| srv_count |  integer  | number of connections to the same service as the current connection in the past two seconds |
| serror_rate   | float  | % of connections that have ``SYN'' errors |
| srv_serror_rate   | float  | % of connections that have ``SYN'' errors    |
| rerror_rate   | float  | % of connections that have ``REJ'' errors    |
| srv_rerror_rate   | float  | % of connections that have ``REJ'' errors    |
| same_srv_rate | float  | % of connections to the same service |
| diff_srv_rate | float  | % of connections to different services   |
| srv_diff_host_rate | float  | % of connections to different hosts |
| dst_host_count    | integer | number of connections having the same destination host (last 100 connections) |
| dst_host_srv_count    | integer | number of connections to the same service as the current connection (to same destination host) |
| dst_host_same_srv_rate    | float   | % of connections to the same service among those to the same host |
| dst_host_diff_srv_rate    | float   | % of connections to different services among those to the same host |
| dst_host_same_src_port_rate   | float   | % of connections to the same port for the same host |
| dst_host_srv_diff_host_rate   | float   | % of connections to the same service coming from different hosts |
| dst_host_serror_rate  | float | % of connections to the same host that have “SYN” errors |
| dst_host_srv_serror_rate  | float   | % of connections to the same service that have “SYN” errors |
| dst_host_rerror_rate  | float   | % of connections to the same host that have “REJ” errors |
| dst_host_srv_rerror_rate  | float   | % of connections to the same service that have “REJ” errors |
| connection_type   | categorical  | target label used for classification    |

## License

Original data by MIT Lincoln Labs and UCI KDD Archive.
This version is released under the [CC BY-NC-SA 4.0](http://creativecommons.org/licenses/by-nc-sa/4.0/) license.
Use for non-commercial research and educational purposes with proper attribution.
