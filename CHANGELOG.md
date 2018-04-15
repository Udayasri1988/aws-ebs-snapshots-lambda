# Change Log

## 0.0.4 [2018-04-14]
### Added
- Using the cross-region script you now can transfer snapshots to other regions. Run it after the creator script, 
waiting at least 20 minutes to be sure snapshots are ready for copying. The new script will delete old snapshots as well.

### Changed
- Introduction of a tag "CreatedOn" with the date. This enables the script for out-of-region to find
snapshots that should be copied.
- Simplified the routine that processes the "KeepForever" tag. 

## 0.0.3 - 2016-05-18
### Added
- Snapshots created by this tool (as opposed to manually) are now indicated
  by the automatic addition of and setting of the tag "Type" to "Automated"
  on each created snapshot.
- Any previously created snapshot can be retained indefinitely by manually 
  adding the tag "KeepForever" to the snapshot to any value.

### Changed
- Cleaned up some code formatting for key/values
- The instance tag "Backup" must now be set explicitly to "Yes" (rather than just being present with any value)
- The snapshot manager skips processing of any snapshots lacking the tag 
  "Type" with a value of "Automated"  
- The instance Name (a standard AWS tag) is now displayed (in parentheses)
  after the InstanceID in log output in the snapshot creator

### Fixed
- Nothing so far

## 0.0.2 - 2016-05-18

### Added
- Second commit based on Ryan S. Brown code that adds support for expiration management
	- https://serverlesscode.com/post/lambda-schedule-ebs-snapshot-backups-2/
	- instances can be tagged with "Retention" tag so we can define how long to keep snapshots around
	- default Retention period, if none specified, is 7 days
	- snapshots are tagged with DeleteOn that contains the day the snapshot should be deleted. 
	  The date is formatted as YYYY-MM-DD (2015-11-05).
	- new snapshot manager function that handles deletion of old snapshots

## 0.0.1 - 2016-05-18

### Added
- Initial commit based on Ryan S. Brown code
	- Sourced from https://serverlesscode.com/post/lambda-schedule-ebs-snapshot-backups/
	- simple snapshots
	- *no* support for expiration
