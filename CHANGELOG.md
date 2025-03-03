# Python GEDCOM Parser - Changelog

## [v1.7.0](https://pypi.org/project/python-gedcom-2/1.7.0/)
### Changes:
- Add all element classes that can have DateElements in them.
- Add EventDetail class to allow inheritance of .get_year_in_date for all new classes.

## [v1.6.0](https://pypi.org/project/python-gedcom-2/1.6.0/)
### Changes:
- Add DateElement - now you can directly and easily get date-related info from a date node in a parsed GEDCOM file.

## [v1.5.0](https://pypi.org/project/python-gedcom-2/1.5.0/)
### Changes:
- Add Parser.get_children() - gets 

## [v1.4.0](https://pypi.org/project/python-gedcom-2/1.4.0/)
### Changes:
- Change top-level package name from gedcom (Which IntelliJ was complaining about) to python_gedcom_2.

## [v1.3.0](https://pypi.org/project/python-gedcom-2/1.3.0/)
### Changes:
- Add Parser.get_element_by_pointer method to more easily access elements that we know are there.
- Fix #4 IndividualElement.criteria_match validity checking fails to catch bad criteria
- Fix #3: Parser.find_path_to_ancestor has a bad check for validity of arguments
- Fix #2: Parser.get_ancestors does not pass down the ancestor_type

## [v1.0.0](https://github.com/nickreynke/python-gedcom/releases/tag/v1.0.0)

### Changes:

- Added `CHANGELOG.md`
- Set source code encoding to UTF-8 explicitly, since for Python 2 ASCII would be the default. For Python 3 the default is UTF-8.
- Separated code of `__init__.py` into individual files, updating the package structure ([#15](https://github.com/nickreynke/python-gedcom/issues/15))
    - Resulted in a new `parser.py` file containing the actual parser, a `element.py` containing the elements the parser can parse and a `tags.py` containing the used GEDCOM tags
- Separated code of new `element.py` into individual modules extending the `Element` class within new submodule `element` to better
  differentiate between the type of `Element`s the parser parses (e.g. `FamilyElement`, `IndividualElement`, ...)
- Added `helpers.py` containing helper functions like a `@deprecated` annotation to annotate methods or classes as
  deprecated. (The helpers may be removed when its contents are no longer used within the project.)
- GEDCOM file is no longer parsed within constructor of `Parser` class (the actual parser; it was named `Gedcom` before).
  The new way to parse is as follows:
  ```python
  # from gedcom import Gedcom   <- Old way of importing the parser
  from python_gedcom_2.parser import Parser

  file_path = '' # Path to your `.ged` file

  # The old way would be to supply the `Parser` (or `Gedcom`) class the `file_path` as its first parameter on initialization
  gedcom_parser = Parser()

  # The new way to parse a GEDCOM file
  gedcom_parser.parse_file(file_path)

  # ...
  ```

### Deprecations:

- `get_individual()` method within `Element` class. Use `to_gedcom_string()` instead.
- `given_match()` method within `IndividualElement` class. Use `given_name_match()` instead.
- `get_burial()` method within `IndividualElement` class. Use `get_burial_data()` instead.
- `get_burial()` method within `IndividualElement` class. Use `get_burial_data()` instead.
- `get_census()` method within `IndividualElement` class. Use `get_census_data()` instead.

### Migrating from v0.2.x to v1.0.0:

The old way of importing the `gedcom` package was like this: `from gedcom import Gedcom`.

The new package code is separated into individual modules within the package. So `Parser` (the actual parser which was named `Gedcom`) would be imported like this:
`from gedcom.parser import Parser`, since the `Parser` class lies within the module `parser` within the package `gedcom`.

Same procedure for the `Element` class: `from gedcom.element.element import Element`, since the `Element` class lies
within the package `gedcom`, the subpackage `element` and the module `element`.

This allows for better maintainability and scalability.

If there are any questions or you encounter a bug please open an issue [here](https://github.com/nickreynke/python-gedcom/issues).

## [v0.2.5dev](https://github.com/nickreynke/python-gedcom/releases/tag/v0.2.5dev)

- Updated project structure ([#18](https://github.com/nickreynke/python-gedcom/issues/18))
- Fixed `setup.py` outputting correct markdown when reading the `README.md` ([#16](https://github.com/nickreynke/python-gedcom/issues/16))
- Applied Flake8 code style and **added explicit error handling**
- Set up test suite

## [v0.2.4dev](https://github.com/nickreynke/python-gedcom/releases/tag/v0.2.4dev)

- Made `surname_match` and `given_match` case insensitive ([#10](https://github.com/nickreynke/python-gedcom/issues/10))
- Added new `is_child` method ([#10](https://github.com/nickreynke/python-gedcom/issues/10))

## [v0.2.3dev](https://github.com/nickreynke/python-gedcom/releases/tag/v0.2.3dev)

- Assemble marriages properly ([#9](https://github.com/nickreynke/python-gedcom/issues/9))
- Return the top NAME record instead of the last one ([#9](https://github.com/nickreynke/python-gedcom/issues/9))

## [v0.2.2dev](https://github.com/nickreynke/python-gedcom/releases/tag/v0.2.2dev)

- Support BOM control characters ([#5](https://github.com/nickreynke/python-gedcom/issues/5))
- Support the last line not having a CR and/or LF
- Support incorrect line splitting generated by Ancestry.  Insert CONT/CONC tag as necessary ([#6](https://github.com/nickreynke/python-gedcom/issues/6))

## [v0.2.1dev](https://github.com/nickreynke/python-gedcom/releases/tag/v0.2.1dev)

- Changed broken links to GEDCOM format specification ([#2](https://github.com/nickreynke/python-gedcom/issues/2))

## [v0.2.0dev](https://github.com/nickreynke/python-gedcom/releases/tag/v0.2.0dev)

- Added `develop` branch to track and update current development process
- Applied PEP 8 Style Guide conventions
- **Renamed variables and methods** to make their purpose more clear
- **Outsourced GEDCOM tags to module level**
- **Added missing inline documentation**
- Optimized `README.md` (sections and better description)
- Added `LICENSE` file
- Cleaned up and optimized code

## [v0.1.1dev](https://github.com/nickreynke/python-gedcom/releases/tag/v0.1.1dev)

- initial release; [forked](https://github.com/madprime/python-gedcom)
