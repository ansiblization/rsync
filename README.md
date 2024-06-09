# Ansible role for installing scheduled rsync jobs

This role depends on the [ansiblization/syslog](https://github.com/ansiblization/syslog) role for logging capabilities.

The rsync jobs to be scheduled have to be defined as a list named `rsync_jobs`:

```yml
rsync_jobs: [{rsync_vars}, ...]
rsync_vars:
    name: "{{ rsync_job.name }}"
    from: "{{ rsync_job.from | default(rsync_job.path) }}"
    to: "{{ rsync_job.to | default(rsync_job.path) }}"
    include: "{{ rsync_job.include | default([]) }}"
    exclude: "{{ rsync_job.exclude | default([]) }}"
    options: "{{ rsync_job.options | default([]) }}"
    schedule: "{{ rsync_job.schedule | default(None) }}"
    conflicts: "{{ rsync_job.conflicts | default([]) }}"
    remote_source: "{{ rsync_job.remote_source | default(None) }}"
    remote_destination: "{{ rsync_job.remote_destination | default(None) }}"
    remote_source_user: "{{ rsync_job.remote_source_user | default('root') }}"
    remote_destination_user: "{{ rsync_job.remote_destination_user | default('root') }}"
    state: "{{ rsync_job.state | default('present') }}"
```
