# External Brightness Control

This is a simple script for managing external monitors brightness through ddc and ddcutil command line tool. It tries to replicate original [brightnessctl](https://github.com/Hummer12007/brightnessctl) tool. See **Usage** to see for more informations.

It requires ddcutil and getopts installed if such are not detected the script will throw errors.

Script will create /tmp/brightnessctl-external files where it will store latest set brightness for each monitor.

## Install

### Manual install

1. Add `brightnessctl-external` script to the PATH
2. Add execution permissions to brightnessctl-external script, example - `chmod +x brightnessctl-external`
3. Run `brightnessctl-external -h` to check if the script was installed correctly

### instal.sh

Run install.sh to automatically install the script in the system - it will automatically install script files in the path in /usr/local/bin/

## Usage

### Get current monitors brightness (-g, --get-brightness)

To print currently set brightness on all detected monitors use `-g` or `--get-brightness` with `brightnessctl-external`. Script will try to detected all connected monitors that are detectable through ddcutil. Example output:

```
> brightnessctl-external -g
D-1 B 90
D-2 B 90
```

### Set new monitors brightness

To set new monitor values use `brightnessctl-external` without any options followed by numeric value. The script will try to set **the same** value to all detectable monitors by ddcutil. Example:

```
> brightnessctl-external 90
# Will set brightness 90 to all monitors
```

During brightness setting the script will save previously set brightness, so that it could be used with `--reset` option later.

### Reset brightness to previous values

To reset values to previous values use `-r` or `--reset` with `brightnessctl-external`. Script will try to set previously set values of brightness to all detectable monitors by ddcutils. Previously set value have to saved - if such value does not exist it will set value `90` **to all monitors**. Example:

```
> brightnessctl-external -r
```

### Help

To print short help information run `brightnessctl-external -h` or `brightnessctl-external --help`.
