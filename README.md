# Kolo

See everything happening in your running Django app. All without leaving VSCode

![status: beta](https://img.shields.io/badge/status-beta-blue) [![vscode downloads](https://img.shields.io/visual-studio-marketplace/i/kolo.kolo)](https://marketplace.visualstudio.com/items?itemName=kolo.kolo) [![vscode last updated](https://img.shields.io/visual-studio-marketplace/last-updated/kolo.kolo)](https://marketplace.visualstudio.com/items?itemName=kolo.kolo) [![Chat on Discord](https://img.shields.io/discord/899363528660635738?label=Chat%20on%20Discord)](https://discord.com/invite/FsTVcFwYUn)

[![vscode extension version](https://img.shields.io/visual-studio-marketplace/v/kolo.kolo?label=VSCode%20extension)](https://marketplace.visualstudio.com/items?itemName=kolo.kolo) [![PyPI version](https://img.shields.io/pypi/v/kolo?label=python%20package)](https://pypi.org/project/kolo/)

![supported python versions](https://img.shields.io/pypi/pyversions/kolo) ![supported django versions](https://img.shields.io/pypi/djversions/kolo?label=django)

Kolo is in beta so there's a chance that you will encounter a problem or bug. When you do, please open an issue on this repository and we'll look into it 🙏


![Annotated Kolo screenshot](https://user-images.githubusercontent.com/7718702/120298398-f3d17800-c2c1-11eb-9052-9adbbff0b5f5.png)


<center>
<h3>DjangoCon Announcement video</h3>
<a href="https://www.youtube.com/watch?v=6XR9Y8v7vZ4" alt="Djangocon youtube video"><img width="300px" src="https://user-images.githubusercontent.com/7718702/120330845-204abb80-c2e5-11eb-92b4-51843ec1e9f1.png"></a>

<em>Kolo launched at DjangoCon Europe 2021</em></center>


## Changelog
Kolo consists of a Python package and a VSCode extension:

- [Changelog for Kolo Python package](./python-package-changelog.md)
- [Changelog for Kolo VSCode extension](./vscode-extension-changelog.md)

### New & Noteworthy features
- The frame visualization now includes a :sparkles: beautiful :sparkles: flame graph that shows timing information for each function call ⏱️

  <img src="https://user-images.githubusercontent.com/7718702/145239425-ad942d9c-b0df-4fb5-b885-4004c80b5694.png" width=500px>
- Show which line of your code caused Django execute a SQL query

  <img width="300px" src="https://user-images.githubusercontent.com/7718702/144677065-8ffa6d46-1130-4a47-b48e-8210e61a0a88.png">

- Significantly simpler Kolo setup if you use Docker for local Django development
- Support for custom request descriptions so that you can easily distinguish different requests even if they arrive at the same path

  <img width="300px" src="https://user-images.githubusercontent.com/7718702/140084399-27e2d472-2b8d-4ff2-80a7-3154730a13c9.png">
- Much improved support for :sparkles: **exceptions** :sparkles: Jump straight to where the problem occurred and see the all the contextual information to understand _why_ it happened

    <img  width="300px" src="https://user-images.githubusercontent.com/7718702/133599943-13502c16-62ef-4e2e-8ac9-5916ff355904.png">
    <br />
    <br />

    <img width="200px" src="https://user-images.githubusercontent.com/7718702/133600081-037413f9-0708-4ef9-aa02-0cf85ca75b46.png">


## Installation
1. Install the python package using
```
pip install kolo
```
2. Add Kolo to the top of your `MIDDLEWARE` in settings.py :
```
"kolo.middleware.KoloMiddleware",
```
3. Make sure DEBUG is True in your settings.py file, then start your local Django server the way you normally would (for example: `python manage.py runserver`)
4. Install the VSCode extension: https://marketplace.visualstudio.com/items?itemName=kolo.kolo
   - Kolo will show up with an icon in the left sidebar in VSCode <img width="40px" src="https://user-images.githubusercontent.com/7718702/120314341-0c965980-c2d3-11eb-9f1d-c3d9bcccd1c9.png">
   - After clicking on the Kolo icon and opening Kolo within VSCode, follow the instructions to login and confirm your email
5. Any new requests that get served by your local, running Django app will now show up in VSCode 🎉
   - Make your Django app serve an HTTP request (for example by going to `localhost:8000`), then return to Kolo in VSCode to inspect it 🔎 🙌

### Minimum requirements
  - VSCode version 1.56 (released April 2021) or newer
  - Python 3.6 or newer
  - Django 2.2 or newer
  - git (Kolo requires git to accurately show line information in VSCode)


### Docker

Kolo supports Docker for local Django development. In many cases, no additional configuration is required for Kolo to work.

Kolo relies on a volume definition to your working directory, which most projects already have configured. If your project does not yet have this configured, then you will need to set this up in order for Kolo to work.

So for example, in your `Dockerfile` you might have something like this specified:

```Dockerfile
WORKDIR /code
COPY . ./
```

And then in your `docker-compose.yml` file, you will need the following corresponding volume definition:

```yml
  volumes:
    - .:/code
```

Kolo works by writing data to a sqlite database from within your running Django app. This volume definition ensures that the `db.sqlite3` file that Kolo stores in the `.kolo` directory is stored not just inside Docker but also on your host operating system, where it can then be read by the Kolo VSCode extension.



### Configuration
Kolo only runs when `DEBUG` is set to `True` in your settings.py file. If you would like to disable Kolo when DEBUG is True, you can set the KOLO_DISABLE environment variable: `KOLO_DISABLE=true`

#### Path To Kolo Directory

If your VSCode workspace folder doesn't contain the `manage.py` file (and the adjacent automatically generated `.kolo` directory) at the top level, then you will need to set the "Path To Kolo Directory" setting in VSCode:

![path to kolo directory setting VSCode](https://user-images.githubusercontent.com/7718702/138758494-65061ad2-797d-4baa-88d6-d2c027a87395.png)

For example, you might have a top level VSCode workspace called "myproject" which has a backend folder that contains your Django app. If `backend` is the folder that includes your `manage.py` file and the `.kolo` directory, then the setting you need to set here is: backend


##### KOLO_PATH

If you don't start your Django app using `python manage.py runserver`, you can make use of the `KOLO_PATH` environment variable to determine the path where Kolo should create the `.kolo` directory. Set `KOLO_PATH` like any other environment variable that your Django app makes use of.


#### .kolo/config.toml

You can specify request paths to be ignored via the `.kolo/config.toml` file:


```toml
# .kolo/config.toml

[filters]
# Kolo will ignore all requests that include /static/ in their path
ignore_request_paths = ["/static/"]

```

If you would like to explicitly include or ignore certain frames, you can also do that:

```toml
# .kolo/config.toml

[filters]
# Kolo will include all frames from the requests library, since each frame's file path would contain /requests/
include_frames = ["/requests/"]

# Kolo will ignore all frames from internal/utils.py
# This would be useful if utils.py does a lot of function calls that you don't particularly care about
ignore_frames = ["internal/utils.py"]

```


By default, Kolo expects the `.kolo` directory to be at the same folder level as your `manage.py` file, but you can specify a custom location for the `.kolo` directory via the `KOLO_PATH` environment variable

#### Custom request description and custom request body formatting

In some cases, just seeing the path of the HTTP request in the sidebar is not sufficient for identifying a request. Say, for example, that your Django app is processing webhook events from Stripe. All those events will arrive at the same path in your app, making it difficult to distinguish different types of events.

The `request-body.js` and `request-description.js` files are here to help us with this!

By default, a set of webhook events from Stripe will look like this:

<img width="400px" src="https://user-images.githubusercontent.com/7718702/140083849-4bd39dff-f1d9-4293-81a4-45ea37867a0a.png">

But if we have the following JavaScript code in our `.kolo/request-description.js` file:
```js
(function () {
  if (
    request.headers.hasOwnProperty("Stripe-Signature")
  ) {
    parsed_body = JSON.parse(request.body)
    return {
      description: parsed_body.type
    }
  }
})();

```

Then, Kolo will show the Stripe event type for each request, making it much easier to distinguish between the different payloads we received from Stripe :tada:

<img width="400px" src="https://user-images.githubusercontent.com/7718702/140084399-27e2d472-2b8d-4ff2-80a7-3154730a13c9.png">

#### request-description.js

Within `.kolo/request-description.js`, a global `request` variable is available. The following fields exist on this variable:
```js
  scheme: string;
  body: string;
  method: string;
  path_info: string;
  headers: {
    [key: string]: string;
  };
```

Kolo expects an object with a top level `description` key to be returned in `request-description.js`, the value of which must be a string. So for example:
```js
return {
  description: "my custom description"
}
```

If you would like to explicitly not have a description for a request, you can `return undefined`


#### request-body.js

`request-body.js` is a useful tool when you'd like to reshape the arriving request body purely for display purposes within Kolo. The code in `.kolo/request-body.js` executes before `request-description.js` meaning that your custom request description code can take adavantage of the reshaped body.

For example, some of the requests a Slack app might receive from Slack have a somewhat unusual format: Slack sends the request with the `x-www-form-urlencoded` content type containing only a single key called "payload" which then contains a JSON string of the actual payload. This request body can be a bit unwieldy, it would be more convenient to directly interact with the JSON payload. This is exactly what `request-body.js` can help us achieve.

The following `.kolo/request-body.js` code converts the payload to just regular JSON for display within Kolo:
```js
(function () {
  if (request.body.startsWith("payload=") && request.headers["User-Agent"].includes("Slackbot")) {
    let request_body;
    try {
      request_body = decodeURIComponent(request.body);
    } catch (err) {
      request_body = request.body;
    }
    const unparsed = request_body.replace("payload=", "");
    const parsed_json_body = JSON.parse(unparsed);

    return {
      body: JSON.stringify(parsed_json_body, null, 2),
      language: "json"
    };
  }
})();
```

Within `.kolo/request-body.js`, a global `request` variable is available. The following fields exist on this variable:
```js
  scheme: string;
  body: string;
  method: string;
  path_info: string;
  headers: {
    [key: string]: string;
  };
```

Kolo expects an object with a top level `body` key to be returned in `request-body.js`, the value of which must be a string:
```js
return {
  body: "my custom body",
}
```

You may also optionally pass a `language` key alongside `body`, which Kolo will pass along to VSCode when viewind the body.

If you would like to explicitly not have a custom request body for a request, you can `return undefined`


## Usage

In VSCode, Kolo is available via the sidebar menu. Once clicked, Kolo shows the requests that your Django app recently served:

<img width="300px" src="https://user-images.githubusercontent.com/7718702/120450412-555c1a00-c388-11eb-9b1f-5169814924a8.png">

From this view you can start exploring your requests and what happened within them. Almost every item in this list is expandable, clickable, and will let you dig into the details

### Inline annotations



<img width="300px" src="https://user-images.githubusercontent.com/7718702/120464889-55aee200-c395-11eb-8545-b50268fb48d0.png">

<img width="400px" src="https://user-images.githubusercontent.com/7718702/120464844-4891f300-c395-11eb-9f86-180317851bea.png">

To enable the inline code annotations for a specific request, click on the top level item in the list of recent requests. You should see a little confirmation message pop up, and then your code will be annotated with inline function arguments, return values, and local variables.


### Frame visualization

<img width="600px" src="https://user-images.githubusercontent.com/7718702/120466598-28fbca00-c397-11eb-9656-062e99a62736.png">


Click on "Frames" for a specific request, and the frame visualization will open up


Check out https://kolo.app for more feature screenshots ✨



## Privacy
During installation, Kolo confirms your email address. This is the only time any information is transmitted from the Kolo VSCode extension to our servers (only your email address is transmitted). Everything else such as your code, or any runtime data stays on your machine and is not transmitted anywhere.

The data Kolo collects at runtime is stored in a local SQLite database on your machine. This same SQLite database is then accessed by the VSCode extension to power all of Kolo's functionality.



## Support
Running into problems? Kolo is in beta, so it's possible you will run into a problem. When you do, please open an issue on this repository or email us: support@kolo.app

Looking for assistance? We're here to help get Kolo set up on your codebase: [Schedule Kolo set up](https://calendly.com/wilhelmklopp)
