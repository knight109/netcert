# netcert

A lightweight command-line tool for checking and inventorying websites you manage or are authorized to monitor. It is intended for routine website maintenance, not vulnerability scanning.

Requires Python 3.10 or newer. Uses only the Python standard library; no packages to install.

## Run

To run it directly from the project directory:

```bash
chmod +x netcert
./netcert --help
```

To use `netcert` as a command on Kali Linux, copy it into a directory on your `PATH`:

```bash
mkdir -p ~/.local/bin
cp netcert ~/.local/bin/netcert
chmod +x ~/.local/bin/netcert
netcert --help
```

If `netcert` is not found, add `~/.local/bin` to your `PATH` for the current shell:

```bash
export PATH="$HOME/.local/bin:$PATH"
```

## Examples

```bash
# Resolve IPv4 and IPv6 addresses
netcert --ip -u example.com

# Check availability for a list of websites
netcert --availability -l sites.txt

# Show basic DNS information
netcert --dns -u example.com

# Collect certificates and write one summary file
netcert --ssl -l sites.txt --store ./certificates --summary

# Run the combined health check
netcert --status -l sites.txt

# Save IP results as JSON or CSV
netcert --ip -l sites.txt --json --save ips.json
netcert --ip -l sites.txt --csv --save ips.csv
```

A target can be a domain, IP address, or `http://` or `https://` URL. A list file contains one target per line; blank lines and lines beginning with `#` are ignored.

## Options

| Option | Description |
| --- | --- |
| `-u`, `--url URL` | Check one target. |
| `-l`, `--list FILE` | Read targets from a text file. Use either `-u` or `-l`. |
| `-i`, `--ip` | Resolve all available IPv4 and IPv6 addresses. |
| `-a`, `--availability` | Check website reachability and report HTTP status and response time. |
| `--dns` | Show resolved addresses, canonical name, and reverse DNS names when available. |
| `--ssl` | Collect the site's peer certificate as a PEM file. Requires `--store`. |
| `--status` | Check IP addresses, availability, and verified SSL health. Does not save certificates. |
| `--store DIRECTORY` | Directory for collected PEM files; only valid with `--ssl`. |
| `--summary` | With `--ssl`, write one `summary.txt` in the store directory. |
| `--save [FILE]` | Save formatted output to a file. Without a filename, uses a default name. Output is also printed. |
| `--json` | Format output as JSON. Cannot be combined with `--csv`. |
| `--csv` | Format output as CSV. Cannot be combined with `--json`. |
| `-h`, `--help` | Show help and examples. |
| `-v`, `--version` | Show the version. |

## Notes

- Select exactly one function per command.
- `--ssl` requires `--store`; `--summary` is only valid with `--ssl`.
- IP and basic DNS results use the operating system's resolver. DNS output is not a full record lookup for types such as MX or TXT.
- Only run checks against websites you own or are authorized to monitor.
