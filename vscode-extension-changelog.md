# VSCode Extension Changelog

_Kolo consists of a python package and a VSCode extension. This is the changelog for the VSCode extension. To view the changelog of the Python package [go here](./python-package-changelog.md)_

_We recommend using the latest version of the kolo python package and VSCode extension. That way you’ll run the most stable and feature-rich versions_

[![vscode extension version](https://img.shields.io/visual-studio-marketplace/v/kolo.kolo?label=VSCode%20extension)](https://marketplace.visualstudio.com/items?itemName=kolo.kolo)

## 1.1.2
_2021-08-18_

- Bundle the extension code, leading to faster startup time and a smaller overall download size
- Include additional sqlite bindings for better support across Linux, Windows, and macOS (including support for Apple Silicon)

## 1.1.1
_2021-08-11_

- Add link to this changelog to the VSCode marketplace page: https://marketplace.visualstudio.com/items?itemName=kolo.kolo

## 1.1.0
_2021-08-11_

- Quite a number of UX improvements
  - The selected invocation is now highlighted in the Kolo sidebar
        ![demo of selected invocation](https://user-images.githubusercontent.com/7718702/128249697-864a5bf9-4d1f-4ac1-98d4-c4a2df9c0cfa.png)
        And the button to "unselect" an invocation is now right next to the selected invocation
  - A new icon in the Frames header to signal that clicking here will open the Frame visualization
  - When clicking into the frames (and thus opening the related code in the editor) the related invocation is automatically selected, showing the inline locals/return value codelenses
- The latest request captured by Kolo is now automatically selected
  - This automatic selecting can be disabled/enabled via the circular button at the top of the sidebar
    ![automatically selecting latest invocation](https://user-images.githubusercontent.com/7718702/128250353-f701ddc6-c799-4acc-8cc2-e8defdffb5d0.png)

## 1.0.7
_2021-08-01_

- Made onboarding experience a little smoother by ensuring you return to the right VSCode window
- Support for VSCode remote workspaces (GitHub Codespaces)

## 1.0.6
_2021-07-30_

- Support for VSCode [untrusted workspaces](https://code.visualstudio.com/blogs/2021/07/06/workspace-trust)


## 1.0.5
_2021-07-26_

- Copy improvements to make the onboarding flow a little bit more smooth

## 1.0.4
_2021-06-08_

- Fix storage path used in Windows, which caused Kolo to be broken on Windows

## 1.0.3
_2021-06-04_

- Introduce setting for specifying the kolo project name (counterpiece to KOLO_PROJECT_NAME in the python package)

## 1.0.2
_2021-06-02_

- Include pre-built versions of sqlite package for linux and windows

## 1.0.1
_2021-06-02_

- Improved the tooltip in the frame visualization
- Improved onboarding copy and flow


## 1.0.0
_2021-06-01_

- Initial release. New to Kolo? Check out [our website](https://kolo.app) and the [announcement video](https://www.youtube.com/watch?v=6XR9Y8v7vZ4)
