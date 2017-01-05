# Ansible Role: manage-software
This is an [Ansible](https://www.ansible.com/) role that helps installing, removing and updating packages.

## Role Variables
Available variables are listed below with example values. By default all values are defined as empty.

Define the list of packages that should be installed:
```
---
pkg_installed:
  - git
  - vim
```

Define the list of packages that should be removed:
```
pkg_removed:
  - vi
```

Define folders where all files are copied to /usr/local/bin:
```
usr_bin_installed: 
  - path/to/some/bin/*
  - path/to/other/bin/*
```

Define folders where all files are copied to /usr/local/sbin:
```
usr_sbin_installed:
  - path/to/some/bin/*
  - path/to/other/bin/*
```

Define the list of bin that should be removed from /usr/local/bin:
```
usr_bin_removed:
  - some-bin-name
```
  
Define the list of sbin that should be removed from /usr/local/sbin:
```
usr_sbin_removed:
  - some-sbin-name
```

Define optional software that is synced to /opt and linked in /usr/local/bin:
```
opt_software_installed:
  - {
    path: "path/to/some/folder", # no / at end
    bin: "opt-bin-name",
    link: "opt-link-name" # name that can be found in PATH
    tasks: "path/to/some/folder/task.yml" # executed if they exist
    }
  - {
      path: "path/to/other/folder",
      bin: "opt2-bin-name" # link defaults to bin if not specified
    }
```

## Example Playbook
You can use a simple playbook like this:
```
---  
- name: "all: ensure software is present in latest version as expected"
  hosts: all
  roles:
    - manage-software
```

## License
BSD 2-Clause License

