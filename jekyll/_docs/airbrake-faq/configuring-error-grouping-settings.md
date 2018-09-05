---
layout: classic-docs
title: Configuring error grouping settings
description: configuring error grouping settings for your project
---

### *Legacy project notice*
*This is the doc for legacy grouping options. Please check out [our current
grouping doc](/docs/features/error-grouping/) for info on how Airbrake groups
errors for non-legacy projects.*

### How do I tell if I have a legacy project?
You can tell by navigating to your project's settings page (click the
"settings" link in your navbar from your project's dashboard). If you see a
small settings page (ie: do not have sections for Global grouping and Strict
grouping above the min app version text box) that doesn't have sections for
custom grouping options, then you have a non-legacy project and should check
out [our current grouping doc](/docs/features/error-grouping/).

If you do have a legacy project, check out the legacy grouping options below.

---

## Default grouping
Airbrake calculates a hash for each error and groups errors with same hash together.
The following attributes are used to calculate the hash:

- error type
- error message with data fields extracted
(see [structured logging](/docs/features/structured-logging))
- function
- file
- line
- environment

### Line shifts

**Line shifts**: When code changes cause an error to occur on a different line in
the file, Airbrake will place the error into the existing error group.

This is a common occurrence and handling line shifts as part of error grouping
avoids creating duplicate errors and notifications, keeping your error dashboard
clean and focused.

## Custom grouping
There are a few exceptions where Airbrake uses different data for the hash, these
are configured per project from the project's settings page.

### Global grouping
*Create Error Groups by error type, don't use default grouping rules*

Errors added to global grouping will be grouped together by **error type**,
differences in error message, component and action, function, and file will
not create new groups.

**e.g.** errors with the same **Error type**, and unique values for everything else will be grouped together.

Global grouping compares hashes based on:

- **error type**
- environment

### Strict grouping
*Create error groups by unique backtrace*

A hash is created from the whole backtrace, not only the line where the error occurred.

**e.g.**
two errors that are exactly the same except for their **backtraces** will now
create 2 groups instead of ending up in the same group

Strict grouping compares hashes based on:

- **backtrace**
- [default grouping rules](#default-grouping)

## Table of grouping rules

---|default|global|strict
---|---|---|---
error type|used|used|used
backtrace| - | - |used
error message| used | - | used
function|used| - |used
file |used| - |used
environment|used|used|used

## Using these settings
To configure an error group to use a custom grouping setting, first identify the
`error type`:

![find error type](/docs/assets/img/docs/airbrake/grouping_settings_error_type.png)

Then input that error's error type in the grouping list you'd like to use and
click the "save" button:

![input error type](/docs/assets/img/docs/airbrake/grouping_settings_text_box.png)

*__Note:__ changing grouping settings is not retroactive. ie: existing errors
will not be regrouped.*

Want to input multiple error types? No problem - just separate entries by
newlines.
