# Python Package Changelog

_Kolo consists of a python package and a VSCode extension. This is the changelog for the `kolo` python package. To view the changelog of the VSCode Extension [go here](./vscode-extension-changelog.md)_

_We recommend using the latest version of the kolo python package and VSCode extension. That way you’ll run the most stable and feature-rich versions_

 [![PyPI version](https://img.shields.io/pypi/v/kolo?label=python%20package)](https://pypi.org/project/kolo/)

## 1.2.1
_2021-10-26_
- Fix issue where Kolo would exhaust iterators as part of processing a frame: https://github.com/kolofordjango/kolo/issues/9

## 1.2.0
_2021-10-25_
- Capture the call site for each captured frame
- Store Kolo database in `.kolo` (alongside the user's working directory) via the `KOLO_STORE_IN_PROJECT=1` environment variable. (To be the default soon)
- Capture information about where in the user code SQL queries originate


## 1.1.3
_2021-09-30_
- Collect `scheme` from the incoming HTTP request which assists the VSCode extension in reliably replaying requests

## 1.1.2
_2021-09-21_
- Fix bug where Kolo would cause additional SQL queries when the evaluation of a third party `__repr__` would call `__repr__` on a django queryset. Specifically this was the case with Django Rest Framework (as with the previous change log item, credit to @vhtkrk for reporting this https://github.com/kolofordjango/kolo/issues/4)

## 1.1.1
_2021-09-20_
- Fix bug where Kolo would prematurely evaluate not-yet-evaluated Querysets (credit to @vhtkrk for reporting this bug!)


## 1.1.0
_2021-09-16_
- Additional configuration options via .kolo/config.toml
  - You can now configure Kolo to exclude certain URL paths (like `/static/`) and also explicitly include and exclude frames based on filepath
- Better support for capturing those exceptions that lead to a 500 error
- Several bug fixes and stability improvements!

## 1.0.4

_2021-08-19_
- Exclude attrs generated frames. The refactor of the 1.0.0 release resulted in these being included, but now they're excluded again!

## 1.0.3

_2021-08-11_

- Add changelog link pointing at this file on PyPI page: https://pypi.org/project/kolo/

## 1.0.2

_2021-08-11_

- Fix classifiers from 1.0.1. Now they actually show up: https://pypi.org/project/kolo/

## 1.0.1

_2021-08-11_

- Add relevant PyPI classifiers: https://pypi.org/classifiers/

## 1.0.0

_2021-08-10_

- Support for Python 3.6
- Refactored how we exclude library code. If you start seeing library code show up in Kolo, please open a new issue on this repo
- Kolo now has better support for showing code that was executed as part of a custom middleware that you have in your Django project
- Kolo will now disable itself if it detects another profiler present (a log message will be shown in this case)
- A whole host of performance and stability improvements
- Introduced more logging to show when Kolo is disabling itself
- Bringing the major version number to 1, to ensure the `kolo` python package and VSCode extension always share the same major version number

## 0.0.5

_2021-06-10_

- Support for Python 3.7

## 0.0.4

_2021-06-04_

- Improve README shown on PyPI

## 0.0.3

_2021-06-04_


- Use INSERT OR IGNORE to prevent bug where the same invocation would be inserted twice into sqlite leading to a confusing user-visible error message

## 0.0.2

_2021-05-26_

- Capture timestamps as floats instead of ints, because we're basically always operating at the sub-second level

## 0.0.1

_2021-05-23_

 - Initial release. New to Kolo? Check out [our website](https://kolo.app) and the [announcement video](https://www.youtube.com/watch?v=6XR9Y8v7vZ4)
