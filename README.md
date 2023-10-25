# Icinga Restic Check

An [Icinga2](https://icinga.com)-Check for [Restic](https://restic.net) deduplicating backup repositories. With this check you can verify if a certain tag has a snapshot within a timeframe.
When one snapshot exceeds the warn timerange (in days), then WARN is set. If one snapshot exceeds the crit timerange (in days) then CRIT is set. Otherwise OK.

You can check multiple snapshots, the result list is checked. The repo is read without setting a lock (so read only), which improves performance. Python3 is needed but no dependencies.

## Options

```./check_restic```

Required options:
- ```-restic_repo_passwordfile```: Sets the location where the repo password file can be found
- ```-restic_repo```: Sets the location of the repository
- ```restic_check_tags```: Which tags are used to filter

Optional:
- ```-restic_bin```: Sets the location where the restic binary is to be found
- ```-restic_compare_date```: The day that should be used to compare, default is now()
- ```-restic_snapshot_age_days_warn```: At what day delta warn should be set
- ```-restic_snapshot_age_days_crit```: At what day delta crit should be set
- ```-restic_compare_date```: Set the date to compare with instead of now (now is default)

- ```-v```: Verbose mode for detailed logs
## Example

```
/check_restic -restic_bin /usr/local/bin/restic -restic_repo_passwordfile /files/.my-restic-password -restic_repo /backup/ -restic_check_tags "website" -restic_compare_date "2023-10-26"
```
