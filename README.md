# SourceMod: Advertisements

This is a simple advertisements plugin. It supports center, chat, hint, menu and top messages.

## Usage

### Types

The following types are supported:

- center: A center message, like sm_csay.
- chat: A chat message, like sm_say. A list of supported colors can be found on https://github.com/PremyslTalich/ColorVariables.
- hint: A hint message, like sm_hsay.
- menu: A menu message, like sm_msay, but without the title or the Exit-option. Pressing 0 will still hide the message, but it will block 1-9 from switching weapons while it's showing.
- top: A top-left message, like sm_tsay. It supports any of the colors listed on https://www.doctormckay.com/morecolors.php, or custom colors with {#abcdef}.

Multiple types per advertisement are allowed, so you can show a different message in multiple places at the same time.

### Message

The message supports the following variables: {currentmap}, {nextmap}, {date}, {time}, {time24} and {timeleft}. Next to that you can print the value of any cvar by enclosing the name with {}, for example {mp_friendlyfire}. Use \n for newlines, which works with center, chat, hint and menu messages.

A couple of examples are given in the supplied advertisements.txt.

### Flags

This field is optional. It accepts a list of flags of players who will not see the advertisement if they have any of those flags. If left empty, only admins will see the advertisement. If omitted everyone will see the advertisement.


## Installation

- Add the compiled plugin `advertisements.smx` to `tf/addons/sourcemod/plugins/`.
- Add the addon configuration file `advertisements.cfg` to `/tf/addons/sourcemod/configs/`.
- Reload all plugins or restart the server.

## Configuration

### AutoExec

```
// Enable/disable displaying advertisements.
// -
// Default: "1"
sm_advertisements_enabled "1"

// File to read the advertisements from.
// -
// Default: "advertisements.txt"
sm_advertisements_file "advertisements.txt"

// Number of seconds between advertisements.
// -
// Default: "30"
sm_advertisements_interval "30"

// Enable/disable random advertisements.
// -
// Default: "0"
sm_advertisements_random "0"

// Display advertisements
// -
// Default: "2.1.3"
sm_advertisements_version "2.1.3"
```
### Plugin

This file *must* be in UTF-8 (without BOM) format for special characters to work.

```
// Types
// -----
// center: Center message
// chat: Chat message
// hint: Hint message
// menu: Menu message
// top: Top message
//
// Flags (optional)
// -----
// Accepts flags of admins that will not see the advertisement.
// When omitted everyone will see the advertisement.
// When left empty only admins will see the advertisement.

"Advertisements"
{
    "1"
    {
        "center"		"www.domain.com"
    }
    "2"
    {
        "center"		"contact@domain.com"
        "hint"			"contact@domain.com"
    }
    "3"
    {
        "menu"			"Next map is {nextmap} in {timeleft} minutes."
        "flags"			"cft"
    }
    "4"
    {
        "chat"			"{green}Current {lightgreen}Map: {default}{currentmap}"
        "flags"			"z"
    }
    "5"
    {
        "top"				"{orange}Admins: friendly fire is {mp_friendlyfire}."
        "flags"			""
    }
}
```
