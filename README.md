![Logo](https://raw.githubusercontent.com/idealista/filebeat_role/master/logo.gif)

[![Build Status](https://travis-ci.com/idealista/filebeat_role.png)](https://travis-ci.com/idealista/filebeat_role)

# Filebeat Ansible role

- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installing](#installing)
- [Usage](#usage)
- [Testing](#testing)
- [Built With](#built-with)
- [Versioning](#versioning)
- [Authors](#authors)
- [License](#license)
- [Contributing](#contributing)

## Getting Started

Ansible role for 7.x/8.x Filebeat. Currently, this works on Debian based linux systems. Tested platforms are:

* Debian 10
* Debian 11

These instructions will get you a copy of the role for your ansible playbook. Once launched, it will install [Filebeat](https://www.elastic.co/products/beats/filebeat).
### Prerequisites

#### To execute this role:

Minimum Ansible version of 2.10.0 and recommended Ansible 5.8.0 version installed.

#### For testing purposes:

* Python 3
* [Molecule](https://molecule.readthedocs.io/)
* [Pipenv](https://github.com/pypa/pipenv)
* [jmespath](http://jmespath.org/)
* [Docker](https://www.docker.com/) as driver
* [Ansible-lint](https://docs.ansible.com/ansible-lint/)


### Installing

Create or add to your roles dependency file (e.g. requirements.yml):

```yaml
- src: idealista.filebeat_role
  version: 1.0.0
  name: filebeat
```

Install the role with ansible-galaxy command:

```
ansible-galaxy install -p roles -r requirements.yml -f
```

Use in a playbook:

```yaml
- hosts: someserver
  roles:
    - role: filebeat
```

## Usage

Look to the [defaults](defaults/main.yml) properties file to see the possible configuration properties.

**You must configure default template and apply basic configuration, for example:**
```yaml
filebeat:
  modules:
  inputs:
  - type: log
    enabled: true
    paths:
      - /var/log/*.log
    encoding: utf8

output:
  elasticsearch:
    hosts: ["elasticsearch-host:9200"]

logging:
  level: info
```
Also, you can see an example on molecule test.

## Testing

```sh
pipenv install -r test-requirements.txt
pipenv run molecule test
```

## Built With

![Ansible](https://img.shields.io/badge/ansible-5.8.0-green.svg)

## Versioning

For the versions available, see the [tags on this repository](https://github.com/idealista/filebeat_role/tags).

Additionally, you can see what change in each version in the [CHANGELOG.md](CHANGELOG.md) file.

## Authors

- **Idealista** - *Work with* - [idealista](https://github.com/idealista)

See also the list of [contributors](https://github.com/idealista/filebeat_role/contributors) who participated in this project.

## License

![Apache 2.0 License](https://img.shields.io/hexpm/l/plug.svg)

This project is licensed under the [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0) license - see the [LICENSE](LICENSE) file for details.

## Contributing

Please read [CONTRIBUTING.md](.github/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.
