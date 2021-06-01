# Kolo

See everything happening in your running Django app. All without leaving VSCode

![status: alpha](https://img.shields.io/badge/status-alpha-blue)

Kolo is in alpha so there's a decent chance that you will encounter a problem or bug. When you do, please open an issue on this repository and we'll look into it 🙏


![Annotated Kolo screenshot](https://user-images.githubusercontent.com/7718702/120298398-f3d17800-c2c1-11eb-9052-9adbbff0b5f5.png)


<center>
<h3>DjangoCon Announcement video</h3>
<a href="https://www.youtube.com/watch?v=6XR9Y8v7vZ4" alt="Djangocon youtube video"><img width="300px" src="https://user-images.githubusercontent.com/7718702/120330845-204abb80-c2e5-11eb-92b4-51843ec1e9f1.png"></a>

<em>Kolo launched at DjangoCon Europe 2021</em></center>




## Installation
1. Install the python package using `pip install kolo`
2. Add Kolo to the top of your `MIDDLEWARE` in settings.py : `"kolo.middleware.KoloMiddleware"`
3. Make sure DEBUG is True in your settings.py file, then start your local Django server the way you normally would (for example: `python manage.py runserver`)
4. Install the VSCode extension: https://marketplace.visualstudio.com/items?itemName=kolo.kolo
   - Kolo will show up with an icon in the left sidebar in VSCode <img width="40px" src="https://user-images.githubusercontent.com/7718702/120314341-0c965980-c2d3-11eb-9f1d-c3d9bcccd1c9.png">
   - After clicking on the Kolo icon and opening Kolo within VSCode, follow the instructions to login and confirm your email
5. Any new requests that get served by your local, running Django app will now show up in VSCode 🎉
   - Make your Django app serve an HTTP request (for example by going to `localhost:8000`), then return to Kolo in VSCode to inspect it 🔎 🙌

### Minimum requirements
  - VSCode version 1.56 (released April 2021) or newer
  - Python 3.8 or newer
  - Django 3.0 or newer
  - git (Kolo requires git to accurately show line information in VSCode)

### Configuration
Kolo only runs when `DEBUG` is set to `True` in your settings.py file. If you would like to disable Kolo when DEBUG is True, you can set the KOLO_DISABLE environment variable: `KOLO_DISABLE=true`



## Privacy
During installation, Kolo confirms your email address. This is the only time any information is transmitted from the Kolo VSCode extension to our servers (only your email address is transmitted). Everything else such as your code, or any runtime data stays on your machine and is not transmitted anywhere.

The data Kolo collects at runtime is stored in a local SQLite database on your machine. This same SQLite database is then accessed by the VSCode extension to power all of Kolo's functionality.



## Support
Running into problems? Kolo is in alpha, so it's quite likely that you will run into a problem. When you do, please open an issue on this repository or email us: support@kolo.app

Looking for assistance? We're here to help get Kolo set up on your codebase: [Schedule Kolo set up](https://calendly.com/wilhelmklopp)

