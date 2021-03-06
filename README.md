# plugin-commands

This is a one-cli plugin that allow to create new commands during runtime to the CLI.

![Build](https://github.com/DNXLabs/plugin-commands/workflows/Build/badge.svg)
[![PyPI](https://badge.fury.io/py/one-cli-plugin-commands.svg)](https://pypi.python.org/pypi/one-cli-plugin-commands/)
[![LICENSE](https://img.shields.io/github/license/DNXLabs/plugin-commands)](https://github.com/DNXLabs/plugin-commands/blob/master/LICENSE)

## Configuration

```yaml
# one.yaml
required_version: ">= 0.7.1"

plugins:
  commands:
    package: one-cli-plugin-commands==0.1.4
    module: 'plugin_commands'

commands:
- name: install
  command: 'npm install'
  volumes: ['.:/work']
  help: 'npm install'
- name: build
  command: 'npm run build'
  volumes: ['.:/work']
  help: 'npm run build'
- name: start
  volumes: ['.:/work']
  command: 'npm start'
  ports: ['4100:4100']
  help: 'npm start'
  environment: ['TEST': 'test']
```

## Usage

```bash
one install
one build
one start
```

## Parameters

```yaml
- name: <command_name>
  image: <string(docker_image)> # default to
  entrypoint: <string(entrypoint)> # default to None
  volumes: <list(volumes)> # ['.:/work', '.:/app']
  command: <string(command)>
  ports: <list(ports)>  # ['3000:3000', '4100:4100']
  environment: <list(environments)> # ['ENV': 'env']
  help: <string(help)>
```

## Development

#### Dependencies

- Python 3

#### Python Virtual Environment

```bash
# Create environment
python3 -m venv env

# To activate the environment
source env/bin/activate

# When you finish you can exit typing
deactivate
```

#### Install dependencies

```bash
pip3 install --editable .
```

## Author

Managed by [DNX Solutions](https://github.com/DNXLabs).

## License

Apache 2 Licensed. See [LICENSE](https://github.com/DNXLabs/plugin-commands/blob/master/LICENSE) for full details.