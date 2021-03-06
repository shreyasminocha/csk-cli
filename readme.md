# CodeSkulptor CLI

Unofficial command-line interface for [CodeSkulptor](https://py3.codeskulptor.org).

## Features

- Downloading user-created files
- Downloading instructor-created files (`comp140`, `examples140`, …)
- Uploading to random URIs (similar to the web interface)
- Uploading to vanity URIs ✨✨

## Installation

```sh
git clone https://github.com/shreyasminocha/csk-cli
cd csk-cli
sudo install ./bin/csk /usr/local/bin/csk
sudo install ./csk.1 /usr/local/share/man/man1/csk.1 # optionally install man page
```

Uninstall:

```sh
sudo rm /usr/local/bin/csk
sudo rm /usr/local/share/man/man1/csk.1
```

## Usage

```
USAGE
    csk SUBCOMMAND FILE [NAME] [OPTIONS]

SUBCOMMANDS
    u | upload		Upload files to CodeSkulptor

        The file (or STDIN if FILE is -), will be uploaded.
        A CodeSkulptor URL will be outputted to STDOUT.

    d | download	Download files from CodeSkulptor

        The file will be downloaded and saved to the path specified
        or outputted to STDOUT if FILE is -.

OPTIONS
    -b		[str]	Bucket ('user306' by default)
    -v		[int]	File version
```

Run `csk --help` for details.

### Examples

```sh
# Download user306_U0CqjtUA8X_0.py
csk download file.py U0CqjtUA8X -v 0
csk download file.py U0CqjtUA8X_0  # alternative

# Download user306_U0CqjtUA8X_4.py
csk download file.py U0CqjtUA8X -v 4
csk download file.py U0CqjtUA8X_4 # alternative

# Output user306_U0CqjtUA8X_0.py to STDOUT
csk download - U0CqjtUA8X -v 0

# Upload example.py to a random URL
csk upload example.py

# Upload example.py to user306_example.py
csk upload example.py example

# Upload example.py to user306_example_7.py
csk upload example.py example -v 7
csk upload example.py example_7 # alternative

# Upload from STDIN to a random URL
csk upload -
```

## Development

The man page is generated using [txt2man](https://github.com/mvertes/txt2man):

```sh
./bin/csk --help | txt2man -t 'CodeSkulptor CLI' -s 1 > csk.1
```

## License

[MIT License](https://l.shreyasminocha.me/MIT/2020-)
