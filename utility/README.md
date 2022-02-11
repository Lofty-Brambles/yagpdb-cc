# Utility

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
{{/* Example of triggering with execCC */}}  

{{$data := sdict
  "Name" "Resource Link Keyword/Embed Title"
  "Embed" (sdict
    "title" "This field overwrites parent Name field in embed title"
    "author" (sdict "name" .User.String)
    "description" "Description field will always be overwritten, regardless of if file is too large"
    "timestamp" currentTime
  )
  "Target" .User
}}

{{execCC CCID nil 0 $data}}
```
```go
{{/* Supports any type target (fully unsupported types will be displayed as JSON) */}}

{{$data := sdict
  "Name" "Custom Target"
  "Target" (sdict
    "KeyName" (cslice "example" "slice")
    "OtherKey" 12345
    "Another" "This one is a string!"
  )
}}

{{execCC CCID nil 0 $data}}
```

Resource keywords are defined [here](./displayData.gotmpl#L105) in the script, and can be edited if desired.  

---

## Emojis

Returns count and list of server emojis in an embed.  

[^1]: As listed in [Wikipedia's extended list of HTML web colours](https://en.wikipedia.org/wiki/Web_colors#Extended_colors)
[^2]: Inspired by Joe's [Display Struct CC](https://yagpdb-cc.github.io/utilities/display-struct) and Devonte's [JSON Converter](https://yagpdb-cc.github.io/utilities/json-converter)
