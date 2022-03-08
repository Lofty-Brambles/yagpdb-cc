# Utility

## Adjust Prefix

Adjusts regular expression (regex) CC triggers to accomodate a server's custom prefix  
Simply run the command with the non-adjusted prefix after the command, and it will adjust the regex to your server's prefix!  

Most common regex trigger formats are taken into account, but the adjusted trigger should always be tested before using.  

---

## Colour Converter

Converts colours from decimal/hex to:  
- Decimal (0-16777215)  
- Hex (0x000000-0xFFFFFF)  
- RGB [(0,0,0)-(255,255,255)]  
- HTML colour name[^1]  

---

## Display Data

Displays target data in a human readable format.[^2]  

This cc essentially recreates the [`json` function](https://docs.yagpdb.xyz/reference/templates/functions#type-conversion), but shows proper field names and is formatted for easy comprehension.  
Like the `json` function, it recursively "deconstructs" a target object and displays each field's name/content.  

It supports being invoked by `execCC`, with `.ExecData` being an sdict (fields shown below). This is helpful for debugging other CCs.  

```go
{{/*
  Supports any type target (fully unsupported types will be displayed as JSON).
  Other configurable values:
    File    : Force file output, equivalent to the -file flag
    Embed   : Other fields to add to the embed -- everything is configurable apart from description
    NoEmbed : Completely remove the regular embed
    NoErr   : If errors occur, exit silently (don't send an error message to the target channel)
*/}}

{{$data := sdict
  "Name" "Custom Target"
  "File" true
  "Target" (sdict
    "KeyName" (cslice "example" "slice")
    "OtherKey" 12345
    "Another" "This one is a string!"
  )
  "Embed" (sdict
    "description" "This will be overwritten"
    "author" (sdict "name" .User.Username "icon_url" (.User.AvatarURL "128"))
    "footer" (sdict "text" "These embed fields are all configurable!")
  )
}}

{{execCC CCID nil 0 $data}}
```
```go
{{/* ExecData can also be any type, name will be set to "ExecData" and output will assume defult parameters */}}
{{$data := 12345}}

{{execCC CCID nil 0 $data}}
```

Resource keywords are defined [here](./displayData.gotmpl#L105) in the script, and can be edited if desired.  

---

## Emojis

Returns count and list of server emojis in an embed.  

---

## Export CC

| WARNING: This will send all your CCs as seperate files/messages, causing spam with a significant number of CCs
| --- |

Exports all your CCs as text files and provides direct download links to each.  
This command, by default, can only be run by administrators.  

To make downloading CCs easier, enable attachment archiving in ticket settings and run this CC in a ticket.  
Upon closing the ticket, it will compile all your CCs as files into a zip archive.  


[^1]: As listed in [Wikipedia's extended list of HTML web colours](https://en.wikipedia.org/wiki/Web_colors#Extended_colors)
[^2]: Inspired by Joe's [Display Struct CC](https://yagpdb-cc.github.io/utilities/display-struct) and Devonte's [JSON Converter](https://yagpdb-cc.github.io/utilities/json-converter)
