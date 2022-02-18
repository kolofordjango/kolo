# VSCode Extension Changelog

_Kolo consists of a python package and a VSCode extension. This is the changelog for the VSCode extension. To view the changelog of the Python package [go here](./python-package-changelog.md)_

_We recommend using the latest version of the kolo python package and VSCode extension. That way you’ll run the most stable and feature-rich versions_

[![vscode extension version](https://img.shields.io/visual-studio-marketplace/v/kolo.kolo?label=VSCode%20extension)](https://marketplace.visualstudio.com/items?itemName=kolo.kolo)

## 1.11.0
_2022-02-18_
- The frame virtual document has been tweaked to show information from both call and return frames
- The language of the frame vdoc is now set to `jupyter` as opposed to `javascript`, which results in several syntax highlighting improvements
- When the return value in the frame vdoc is valid JSON, then it will now be pretty-printed

## 1.10.0
_2022-01-15_
- Indicate which SQL queries are duplicate in the "SQL Queries made" view

  <img src="https://user-images.githubusercontent.com/7718702/149631547-b57a0ed3-db96-4ebc-9e89-d7e7c0ca2e38.png" width=500px>

## 1.9.1
_2022-01-01_
- Fixed a bug where opening the file/line where a SQL query was made led to "file not found" errors, because the `kolo.pathToKoloDirectory` setting was not respected. Thanks to @court-js for the report :bow: https://github.com/kolofordjango/kolo/issues/11
 
## 1.9.0
_2021-12-07_
- The frame visualization now includes a :sparkles: beautiful :sparkles: flame graph that shows timing information for each function call ⏱️ 

  <img src="https://user-images.githubusercontent.com/7718702/145239425-ad942d9c-b0df-4fb5-b885-4004c80b5694.png" width=500px>

## 1.8.0
_2021-12-03_
- Show where in your code each SQL query originated


  <img src="https://user-images.githubusercontent.com/7718702/144677065-8ffa6d46-1130-4a47-b48e-8210e61a0a88.png" width=300px>
- Fix bug where in some cases it was impossible to interact with leaf nodes in the tree visualization


## 1.7.0
_2021-11-03_
- Support for custom request descriptions so that you can easily distinguish different requests even if they arrive at the same path

  <img width="300px" src="https://user-images.githubusercontent.com/7718702/140084399-27e2d472-2b8d-4ff2-80a7-3154730a13c9.png">

## 1.6.0
_2021-10-29_
- Increase the number of recent requests shown from 5 to 10
- Add pagination to look over requests older than the last 10
 
## 1.5.1
_2021-10-27_
- Ensure Kolo can run on Apple Silicon

## 1.5.0
_2021-10-25_
- Read Kolo data from `.kolo/db.sqlite3` instead of from the OS specific user data directory (to become the default soon). More details here: https://github.com/kolofordjango/kolo/issues/8
- Added the "Path to Kolo Directory" setting which specifies the path to the `.kolo` folder (:point_up:) as well as helping Kolo understand at which place to open files. Particularly useful if you're using Docker or if your VSCode workspace does not contain the `.kolo` directory at the top level

## 1.4.1
_2021-10-2_
- Update dependencies

## 1.4.0
_2021-10-18_
- Add section in sidebar with quick links to documentation and Discord

## 1.3.0
_2021-09-30_
- Add support for replaying HTTP requests ⏪

  https://user-images.githubusercontent.com/7718702/135449686-815bc247-4cb3-4fb4-8526-8a67ed6fd743.mov

## 1.2.0
_2021-09-16_
- Much improved support for :sparkles: **exceptions** :sparkles: Jump straight to where the problem occurred and see the all the contextual information to understand _why_ it happened
 
    <img  width="300px" src="https://user-images.githubusercontent.com/7718702/133599943-13502c16-62ef-4e2e-8ac9-5916ff355904.png">
    <br />
    <br />
    
    <img width="200px" src="https://user-images.githubusercontent.com/7718702/133600081-037413f9-0708-4ef9-aa02-0cf85ca75b46.png">

## 1.1.3
_2021-09-12_
- Improve the UX of selecting a frame from the visualization 
  - Clicking on a frame in the visualization will now open the code in such a way that you don't have to manually re-arrange tabs to continue exploring
- Fig bug where an invocation wouldn't load if we couldn't find a corresponding HTTP response for an outgoing HTTP request

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
