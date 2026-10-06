# netcert

A lightweight command-line tool for checking and inventorying websites you manage or are authorized to monitor. It is intended for routine website maintenance, not vulnerability scanning.

Requires Python 3.10 or newer. Uses only the Python standard library; no packages to install.

## Download & Run

Clone the repository:

```bash
git clone https://github.com/knight109/netcert.git
cd netcert
chmod +x netcert
./netcert --help
```

To use `netcert` as a command on Kali Linux:

```bash
mkdir -p ~/.local/bin
cp netcert ~/.local/bin/netcert
chmod +x ~/.local/bin/netcert
```

If `~/.local/bin` is not in your `PATH`:

```bash
export PATH="$HOME/.local/bin:$PATH"
```

You can now run:

```bash
netcert --help
```

## Options

| Option                 | Description                                                                                       |
| ---------------------- | ------------------------------------------------------------------------------------------------- |
| `-u`, `--url URL`      | Check one target.                                                                                 |
| `-l`, `--list FILE`    | Read targets from a text file. Use either `-u` or `-l`.                                           |
| `-i`, `--ip`           | Resolve all available IPv4 and IPv6 addresses.                                                    |
| `-a`, `--availability` | Check website reachability and report HTTP status and response time.                              |
| `--dns`                | Show resolved addresses, canonical name, and reverse DNS names when available.                    |
| `--ssl`                | Collect the site's peer certificate as a PEM file. Requires `--store`.                            |
| `--status`             | Check IP addresses, availability, and verified SSL health. Does not save certificates.            |
| `--store DIRECTORY`    | Directory for collected PEM files; only valid with `--ssl`.                                       |
| `--summary`            | With `--ssl`, write one `summary.txt` in the store directory.                                     |
| `--save [FILE]`        | Save formatted output to a file. Without a filename, uses a default name. Output is also printed. |
| `--json`               | Format output as JSON. Cannot be combined with `--csv`.                                           |
| `--csv`                | Format output as CSV. Cannot be combined with `--json`.                                           |
| `-h`, `--help`         | Show help and examples.                                                                           |
| `-v`, `--version`      | Show the version.                                                                                 |
