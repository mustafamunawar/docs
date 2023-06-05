# YAML

- YAML stands for `YAML Ain't Markup Language`, but it originally stood for `Yet Another Markup Language`.

- YAML is a human-readable data serialization language that is often used for writing configuration files.

- `Serialization` is a process where one application or service that has different data structures and is written in a different set of technologies can transfer data to another application using a standard format.

- `serialization` is about translating, converting, and wrapping up a data structure in another format.

- XML, JSON, and YAML are all used for creating configuration files and transferring data between applications.

- YAML is often used as a format for configuration files, but its object serialization abilities make it a viable replacement for languages like JSON.

- YAML files use a .yml or .yaml extension.

- YAML is an official strict superset of JSON `despite looking very different from JSON`.

- YAML allows comments(start with "#"). Note that JSON doesn't allow comments.

- YAML is also a superset of JSON, so JSON files are valid in YAML. However, note that newlines and indentation actually mean something in YAML, as opposed to JSON, which uses brackets and braces.

- Like JSON, Key/value pairs are the building blocks of YAML documents.

- YAML files use `Python-style indentation` to determine the structure and indicate nesting. `Tab characters are not allowed for indentation` by design, to maintain portability across systems, so whitespaces—literal space characters—are used instead.

- Whitespace is part of YAML's formatting. Unless otherwise indicated, newlines indicate the end of a field. You structure a YAML document with indentation. The indentation level can be one or more spaces. The specification forbids use of tabs.

- A comment begins with pound or hash symbol `#`.

- No multiline comments.

- Three dashes `---` are used to signal the start of a document

- Three dots `...` can be used to signal the end of a document (it is optional)

- YAML supports multiple documents in a single file, and compliant parsers will recognize each set of three-dashes as the beginning of a new one.

- The structure of a YAML file is a `map` or a `list`, and it follows a hierarchy depending on the `indentation`, and `how you define your key values`.

- In YAML, there is an emphasis on `indentation and line separation` to denote `levels and structure` in data. The indentation system is quite similar to the one Python uses.

- YAML doesn't use symbols such as curly braces-{}, square brackets-[], or opening or closing tags - just indentation.

- Although YAML auto-detects the data types in a file, you can specify the type of data you want to use.

- To explicitly specify the type of data, use the !! symbol and the name of the data type before the value:
  `date: !!str 2022-11-11` or `fave_number: !!float 1`

## From JSON to YAML

```json
{
  "doe": "a deer, a female deer",
  "ray": "a drop of golden sun",
  "pi": 3.14159,
  "xmas": true,
  "french-hens": 3,
  "calling-birds": ["huey", "dewey", "louie", "fred"],
  "xmas-fifth-day": {
    "calling-birds": "four",
    "french-hens": 3,
    "golden-rings": 5,
    "partridges": {
      "count": 1,
      "location": "a pear tree"
    },
    "turtle-doves": "two"
  }
}
```

- using https://www.json2yaml.com/ site the above JSON is converted to following YAML

```yaml
---
doe: a deer, a female deer
ray: a drop of golden sun
pi: 3.14159
xmas: true
french-hens: 3
calling-birds:
  - huey
  - dewey
  - louie
  - fred
xmas-fifth-day:
  calling-birds: four
  french-hens: 3
  golden-rings: 5
  partridges:
    count: 1
    location: a pear tree
  turtle-doves: two
```

- A YAML `collection` be:

  - a `sequence` (equivalent to a list or array)
  - a `mapping` (equivalent to a dictionary, hashes or object)

- A `sequence` in YAML coressponds to JS `array` or python `list`.

- Each item (element) of a `sequence` is written on a separate line and should start with a dash (-) followed by a space and then the item's value.

- And each item in the list should be on the same level of indentation.

```yaml
- HTML
- CSS
- JavaScript
```

- A YAML `mapping` allows you to list keys with values.

```yaml
Employee:
  name: John Doe
  age: 23
  country: USA
```

or a sequence (array) of employees (note each employee is a mapping or object/dictionary):

```yaml
Employees:
  - name: John Doe
    department: Engineering
    country: USA
  - name: Kate Kateson
    department: IT support
    country: United Kingdom
```
