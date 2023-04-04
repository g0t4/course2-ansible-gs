## notes

- [release docs](https://docs.ansible.com/ansible/devel/reference_appendices/release_and_maintenance.html)
- FYI for `docs.ansible.com` links, switch to `devel` branch (not `latest`) to get the most recent roadmap, changelogs, porting guides, etc

## porting guides

- [porting guides docs](https://docs.ansible.com/ansible/devel/porting_guides/porting_guides.html)
- [github `rst` files](https://github.com/ansible/ansible/tree/devel/docs/docsite/rst/porting_guides)
    - *** core porting guides are brief and often underscore major changes - worth reading

## roadmaps

- [github `rst` files](https://github.com/ansible/ansible/tree/devel/docs/docsite/rst/roadmap)
- [`core` roadmap docs](https://docs.ansible.com/ansible/devel/roadmap/ansible_core_roadmap_index.html)
    - *** short
- [`community package` roadmap docs](https://docs.ansible.com/ansible/devel/roadmap/ansible_roadmap_index.html)

## release cycle

- [`core`](https://docs.ansible.com/ansible/devel/reference_appendices/release_and_maintenance.html#ansible-core-release-cycle)
- [`community package`](https://docs.ansible.com/ansible/devel/reference_appendices/release_and_maintenance.html#ansible-community-package-release-cycle)

## changelogs

- `core`: linked via the [release support matrix](https://docs.ansible.com/ansible/devel/reference_appendices/release_and_maintenance.html#ansible-core-support-matrix), click version number link
    - links to files in ansible/ansible repo in branch named stable-2.X, i.e.: [2.15](https://github.com/ansible/ansible/blob/stable-2.15/changelogs/CHANGELOG-v2.15.rst), [2.14](https://github.com/ansible/ansible/blob/stable-2.14/changelogs/CHANGELOG-v2.14.rst), [2.13](https://github.com/ansible/ansible/blob/stable-2.13/changelogs/CHANGELOG-v2.13.rst), [2.12](https://github.com/ansible/ansible/blob/stable-2.12/changelogs/CHANGELOG-v2.12.rst), [2.11](https://github.com/ansible/ansible/blob/stable-2.11/changelogs/CHANGELOG-v2.11.rst), [2.10](https://github.com/ansible/ansible/blob/stable-2.10/changelogs/CHANGELOG-v2.10.rst)
        - *** a bit more in-depth than core porting guides, but still manageable to read/skim 
- `community package`: see [ansible-build-data repo](https://github.com/ansible-community/ansible-build-data)
    - each version has a folder with two key files:
        - `CHANGELOG-v*.rst`, i.e. [CHANGELOG-v7.rst](https://github.com/ansible-community/ansible-build-data/blob/main/7/CHANGELOG-v7.rst)
            - these are insanely long, read as needed
        - FYI, there are also redundant copies of the porting guides named `porting_guide_X.rst`, i.e: [porting_guide_7](https://github.com/ansible-community/ansible-build-data/blob/main/7/porting_guide_7.rst)
    - [changelogs also linked here to `ansible-build-data` repo](https://docs.ansible.com/ansible/devel/reference_appendices/release_and_maintenance.html#ansible-community-changelogs)

