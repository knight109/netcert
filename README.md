# netcert

A lightweight command-line tool for checking and inventorying websites you manage or are authorized to monitor. It is intended for routine website maintenance, not vulnerability scanning.

Requires Python 3.10 or newer. Uses only the Python standard library; no packages to install.

## Download

Clone the repository:

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
cd REPOSITORY
```

Or, if you only want the `netcert` file, download it directly from the repository and make it executable:

```bash
chmod +x netcert
```

Then run:

```bash
./netcert --help
```


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
