# OpenVPN Alias
## Runs an OpenVPN connection in a new Tmux session

Useful for running VPN connections in the background

Steps:
* Copy the alias into you `~/.bash_aliases`
  - Replace the `<PATH-TO-CONFIG>` with the path to your `.ovpn` config file
* Use `source ~/.bashrc` to resource the aliases file
* Start the connection with the `vpn` command
* Once the connection is initialised, use `Ctrl + D` to detach from the session. 
* When you want to close the connection, use `tmux a -t VPN` to re-attach to the session, then use `Ctrl + C` to exit as normal

To use the alias for multiple connection packs, just change the alias name, Tmux session name and path to the config.
