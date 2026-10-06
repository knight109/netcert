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

Update
```bash
cd netcert
git pull
```