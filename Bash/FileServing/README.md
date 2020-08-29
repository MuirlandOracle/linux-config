# FileServing Aliases

* Used to transfer files between your Linux machine and a target
* Requires an `impacket` installation in `/opt`
  - `sudo git clone https://github.com/SecureAuthCorp/impacket /opt`
* Best used with a directory called `/commontools` in `/`, containing symlinks to anything you want to serve quickly

### Usage:
* Add the aliases into you `~/.bash_aliases` file
* Re-source your `bashrc` with `source ~/.bashrc`
* Use the aliases as added:
  - `up`
  - `servecommon`
  - `smbserv`
  - `smbcommon`
