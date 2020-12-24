# Debian Desktop XFCE with PyCharm & Atom as IDE for Python (Vagrant)

## Installation

### Intall Vagrant and VirtualBox

- [Download & install VirtualBox](https://www.virtualbox.org)
- [Download & install Vagrant](https://www.vagrantup.com)

#### Intall required plugins

- `vagrant plugin install vagrant-vbguest`

## Provision

- Put your provisioning into `projects.yml`.
- `vagrant up`

## Usage

When you bring up your machine, default user and password are:

- User: `debian`
- Password: `debian`

Note: You can customize it on `debian_desktop/defaults/main`.

## Credits

* [Andrey Saksonov](https://saksonov.me) - [Original GitHub repo](https://github.com/andreysaksonov/vagrant_debian-desktop)
* [@DavidDataScience](https://hackernoon.com/u/DavidDataScience) - [Setting up Atom as a Python IDE [A How To Guide]](https://hackernoon.com/setting-up-atom-as-a-python-ide-a-how-to-guide-o6dd37ff)
