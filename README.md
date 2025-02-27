# google-translate

A **free** and **unlimited** API for Google Translate

Parts of the code are ported from [gtranslate](https://github.com/bregydoc/gtranslate) and [google-translate-api](https://github.com/matheuss/google-translate-api) (also MIT license).

## Notice

This fork is for testing purpose, tracking the [original repo](https://github.com/gilang-as/google-translate) for updates.

## Features
- Auto language detection
- Spelling correction
- Language correction
- Fast and reliable – it uses the same servers that [translate.google.com](https://translate.google.com) uses

## Install

```
go get github.com/elvuel/google-translate
```

## API

### Example
```go
package main

import (
	"encoding/json"
	"fmt"
	gtranslate "github.com/elvuel/google-translate"
)

func main()  {
	translated, err := gtranslate.ManualTranslate("Welcome back", "en-US", "zh-CN")
	if err != nil {
		panic(err)
	} else {
		prettyJSON, err := json.MarshalIndent(translated, "", "\t")
		if err != nil {
			panic(err)
		}
		fmt.Println(string(prettyJSON))
	}
}
```

### Returns an `object`:
- `text` *(string)* – The translated text.
- `pronunciation` *(string)* – The Pronunciation text.
- `from` *(object)*
    - `language` *(object)*
        - `did_you_mean` *(boolean)* - `true` if the API suggest a correction in the source language
        - `iso` *(string)* - The code of the language that the API has recognized in the `text`
    - `text` *(object)*
        - `auto_corrected` *(boolean)* – `true` if the API has auto corrected the `text`
        - `value` *(string)* – The auto corrected `text` or the `text` with suggested corrections
        - `did_you_mean` *(boolean)* – `true` if the API has suggested corrections to the `text`

## License

MIT © [Gilang Adi S](https://github.com/gilang-as)
