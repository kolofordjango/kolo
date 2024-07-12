# Kolo

Trace and visualize your Python code. Generate working tests. 

[![downloads](https://img.shields.io/pypi/dm/kolo)](https://pypi.org/project/kolo/) [![Chat on Discord](https://img.shields.io/discord/899363528660635738?label=Chat%20on%20Discord)](https://discord.com/invite/FsTVcFwYUn)

[![PyPI version](https://img.shields.io/pypi/v/kolo?label=python%20package)](https://pypi.org/project/kolo/) [![supported python versions](https://img.shields.io/pypi/pyversions/kolo)](https://pypi.org/project/kolo/)

📋 [docs.kolo.app](https://docs.kolo.app)


<img width="1283" alt="image" src="https://github.com/kolofordjango/kolo/assets/7718702/f332094d-a779-4d14-bd5c-1e0db4b2037e">
<p align="center"><sup>Screenshot of Kolo from the <a href="https://github.com/kolofordjango/todo-demo">Todo Demo app</a></sup></p>


## Quickstart

Getting started with Kolo only takes a couple of minutes. The fastest way to understand what Kolo does and how it can be helpful is by trying it out on a codebase you work on. But if you're in a hurry or can't try Kolo on your own codebase, you can preview some functionality in our [playground](https://play.kolo.app).


### Trace a Django request

*Trace a Django request for inspection, visualization, and debugging purposes.*


1. Install kolo using `pip install kolo`
2. Add `"kolo.middleware.KoloMiddleware"` to the top of your MIDDLEWARE list in settings.py
3. Start your Django server using `python manage.py runserver` and make a request to any page.
4. Browse to `localhost:8000/_kolo/` to view your traced request. It should look similar to the screenshot at the top of the page 🚀


(For a more in-depth version of this tutorial see [How to: Trace Django requests](https://docs.kolo.app/en/latest/howto/trace-django-requests.html))


### Generate a test from your trace
*Now that we have a trace recorded, we can generate a working integration test from that trace.*

1. Navigate from the "Trace" page to the "Test" page.

<img width="1446" alt="image" src="https://github.com/kolofordjango/kolo/assets/7718702/b63347f0-def2-4abb-ad12-ee298afec21c">

2. You'll see a page similar to the screenshot above, with your integration test waiting for you 🥳
3. Save the test file to your desired location or copy/paste it manually.
4. Then run the test in the same way you normally would to check that it's working. Make any edits as desired.


#### Customizing test generation
Every codebase has different testing requirements and code style. You can customize Kolo's test generation to suit your needs. Learn more about how to do this in [How to: Customize test generation](https://docs.kolo.app/en/latest/howto/customize-testgen.html)


#### How does test generation work?

Based on the data captured in the trace, Kolo first generate a test plan which includes the various "steps" it intends to include in the integration test. Each step in the plan is derived from some information in the trace itself. Then, based on the plan, Kolo then generates the test code on the left of the page. Learn more about how Kolo test generation works in [this blog post](https://blog.kolo.app/tests-no-joy.html)





## Support

If you have any questions or trouble getting set up with Kolo, please get in touch with us. We're here to help and would love any feedback!

* [Talk to us on Discord](https://discord.com/invite/FsTVcFwYUn)
* [Create an issue](https://github.com/kolofordjango/kolo/issues/new/choose)
* [Email us](mailto:support@kolo.app)
* [Schedule a meeting with us to help get Kolo set up](https://calendly.com/wilhelmklopp)


## Screenshots

What Kolo looks like when used with a real world Django application ([Simple Poll](https://simplepoll.rocks))

#### Viewing a trace
<img width="1283" alt="image" src="https://github.com/kolofordjango/kolo/assets/7718702/16caa182-a496-497c-b9cd-6ae3f4029c36">


#### Exploring a trace
<img width="1800" alt="image" src="https://github.com/kolofordjango/kolo/assets/7718702/cb78ce41-cd54-411c-bfac-40b6d914b935">

#### Viewing an SQL query
<img width="1797" alt="image" src="https://github.com/kolofordjango/kolo/assets/7718702/b2224463-652b-4bbe-a414-ed2bd2e6db27">


#### Viewing a function call
<img width="1799" alt="image" src="https://github.com/kolofordjango/kolo/assets/7718702/669f67ff-3740-4ce1-95f6-75b2ce0245fa">


#### Generating an integration test

<img width="1797" alt="image" src="https://github.com/kolofordjango/kolo/assets/7718702/62d9c154-fa79-44f1-8d01-d3a8e93cecd5">

