# Role Name

This role implements management of Gentoo overlays on the managed host. The role uses `eselect-repository` to manipulate the requested repository.

# Requirements

The role uses `json_query`, which requires installation of `jmespath`.

# Role Variables

* `gentoo_overlay_repos`: list of repositories to add/remove. Example:

```yaml
# Adds guru overlay.
gentoo_overlay_repos:
  - name: guru
    state: present
```

`state` can be one of "present", "disabled", "absent". "present" is the default value.

State transition table:

| Source state | Target state | Action |
| --- | --- | --- |
| any | present | `eselect repository enable <name>` |
| present | disabled | `eselect repository disable <name>` |
| any | absent | `eselect repository remove <name>` |

* `gentoo_overlay_mask_by_default`: whether to mask packages from repos that were enabled (add "`*/*::repo.name`" to package.mask). Set to `true` by default.

# Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

# License

BSD

# Limitations

* The current version only supports addition/removal of overlays from the [official list](https://repos.gentoo.org/).
