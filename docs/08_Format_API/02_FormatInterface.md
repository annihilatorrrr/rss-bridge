The `FormatInterface`interface defines functions that need to be implemented by all formats:

* [display](#the-display-function)
* [stringify](#the-stringify-function)
* [setItems](#the-setitems-function)
* [getItems](#the-getitems-function)
* [setCharset](#the-setcharset-function)
* [getCharset](#the-getcharset-function)
* [setExtraInfos](#the-setextrainfos-function)
* [getExtraInfos](#the-getextrainfos-function)
* [getMimeType](#the-getmimetype-function)

Find a [template](#template) at the end of this file

# Functions

## The `stringify` function

The `stringify` function returns the items received by [`setItems`](#the-setitem-function) as string.

```PHP
stringify(): string
```

## The `setItems` function

The `setItems` function receives an array of items generated by the bridge and must return the object instance. Each item represents an entry in the feed. For more information refer to the [collectData](../05_Bridge_API/02_BridgeAbstract.md#collectdata) function.

```PHP
setItems(array $items): self
```

## The `getItems` function

The `getItems` function returns the items previously set by the [`setItems`](#the-setitems-function) function. If no items where set previously this function returns an error.

```PHP
getItems(): array
```

## The `setCharset` function

The `setCharset` function receives the character set value as string and returns the object instance.

```PHP
setCharset(string): self
```

## The `getCharset` function

The `getCharset` function returns the character set value.

```PHP
getCharset(): string
```

## The `setExtraInfos` function

The `setExtraInfos` function receives an array of elements with additional information to generate format outputs and must return the object instance.

```PHP
setExtraInfos(array $infos): self
```

Currently supported information are:

Name | Description
-----|------------
`name` | Defines the name as generated by the bridge
`uri` | Defines the URI of the feed as generated by the bridge

## The `getExtraInfos` function

The `getExtraInfos` function returns the information previously set via the [`setExtraInfos`](#the-setextrainfos-function) function.

```PHP
getExtraInfos(): array
```

## The `getMimeType` function

The `getMimeType` function returns the expected [MIME type](https://en.wikipedia.org/wiki/Media_type#Common_examples) of the format's output.

```PHP
getMimeType(): string
```

# Template

This is a bare minimum template for a format:

```PHP
<?php
class MyTypeFormat implements FormatInterface {
    private $items;
    private $charset;
    private $extraInfos;

    public function stringify(){
        // Implement your code here
        return ''; // Return items as string
    }

    public function setItems(array $items){
        $this->items = $items;
        return $this;
    }

    public function getItems(){
        return $this->items;
    }

    public function setCharset($charset){
        $this->charset = $charset;
        return $this;
    }

    public function getCharset(){
        return $this->charset;
    }

    public function setExtraInfos(array $infos){
        $this->extraInfos = $infos;
        return $this;
    }

    public function getExtraInfos(){
        return $this->extraInfos;
    }
}
// Imaginary empty line!
```