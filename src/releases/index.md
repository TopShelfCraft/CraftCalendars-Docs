---
title: Changelog
type: releases
order: 0
---

### 1.1.7

- Fixed a bug where parameters passed as an Array to `EventCriteriaModel` were ignored. (How rude.)
- Implemented the `repeats` and `repeatsForever` parameters on `EventCriteriaModel`.
- Added a resource call to ensure that Timepicker JS loads before Calendars JS, to prevent an obscure error that might occur if Calendars fields are rendered before any other date/time inputs.
- Added a temporary workaround for an issue where Schedule Rules Editor components aren't rendered for newly created Commerce Variants.
- Updated Knockout JS library to v3.4.0.
- Fixed some typos in comments.

### 1.1.6

- Fixed a bug where the `calendar` attribute on an `EventCriteriaModel` wouldn't be parsed correctly if the user passed in a CalendarCriteriaModel.
- Changed how the `EventCriteriaModel` spins up its internal Element Type stash to _really_ prevent database errors from occurring when querying events from third-party Element Types.

### 1.1.5

- Fixed a bug that caused a SQL 'missing column' error when using the Event Dates fieldtype with non-Entry element types.

### 1.1.4

- Source dates for recurrence generation are now converted to the system DateTimeZone before recurrences are calculated, to avoid DST offset issues that could arise when converting UTC dates to the system timezone in templates.

### 1.1.3

- Disabled the FieldType from being rendered in contexts where there is no element attached, such as in Quick Post widgets, to avoid PHP errors. (This is a highly dissatisfying solution and will hopefully be short-term.)

### 1.1.2

- Corrected some confusion between the `id` and `ownerId` attributes that caused Event Dates fields to display selected dates from other entries.
- Fixed a version number typo that caused Craft to detect available updates even when the plugin was up-to-date.

### 1.1.0

- Added the `totalEvents()` method to `EventCriteriaModel`, which provides a count of all events generated by a criteria without accounting for `eventOffset` or `eventLimit`

### 1.0.2

- Added a spiffy new plugin icon for the Settings page.
- Fixed an issue where `firstEvent()` and `lastEvent()` did not return correct results.
- Refactored matched owner caching so `getOwnerIds()` works even if it is called before the event generator has been invoked.
- Fixed an issue where setting the `ownerId` parameter on an `EventCriteriaModel` didn't properly filter the results.

### 1.0.1

- This release marks the end of the public beta. Craft Calendars is now commercially supported!
- Fixed issues with localization of datepicker and timepicker fields.
- Added CSRF-prevention token in New/Edit Calendar CP form.
- Fixed an error that could occur when a Task tried to save a field whose input data was empty.

### 0.8.3 / 1.0.0

- Fixed a bug that would cause a 'missing method' error when creating a new calendar.
- Fixed a bug that prevented events from being properly returned on a monthly calendar unless a dateRangeEnd was explicitly supplied.

### 0.8.2

- Fixed a bug that would cause a database error during installation.

### 0.8.0 / 0.8.1

Version 0.8.x introduces some breaking changes from previous Beta versions. Please see the [Updating from Beta](/guide/updating-from-beta.html) page before updating to this version. 

- Craft Calendars requires Craft 2.5+
- `calendars.eventData` is deprecated, replaced by _calendars.events_, which returns a brand new _EventCriteriaModel_.
- `calendars.calendars` returns a nice _CalendarsCriteriaModel_.
- `EventDataCrtieriaModel` is dead, replaced by the much nicer _EventCriteriaModel_.
- `calendars.month` has new properties and methods, attaches events much more efficiently, and renders faster, thanks to the new `CalendarMonthModel`.
- _EventCriteriaModel_ allows ordering events by multiple criteria
- _EventDataModel_ is dead, replaced by the much nicer _EventModel_.
- Recurrences are only calculated for the needed date range, resulting in dramatic speed improvements
- **Event Dates** fields return an entire _EventCriteriaModel_ rather than just a starting _DateTime_.
- **Event Dates** fields play nicely in Live Preview and saved drafts.

### 0.6.4

- Forced EventDataService to fetch event data with related records attached
- Implemented event ordering
- Bug fixes

### 0.6.3

- Fixed a bug in PHP 5.3 and 5.4 where the system was operating on a \DateTime object when it expected a \Craft\DateTime object.
- Changed the default behavior of DT() to throw an Exception if its parameter isn't a recognized format.

### 0.6.2

- Added a double-check to the `calendars.month` logic to avoid PHP notices if an item was missing or mis-keyed in the dates array.
- Made the `calendars.month` tag's reference _EventDataCriteriaModel_ available as the `eventData` property.
- Fixed a stupid, stupid typo that caused only the last registered Element to be fetched and attached to its events.
- Made an EventDataCriteriaModel's debug data available with the `debug()` getter method.

### 0.6.1

- First beta release
