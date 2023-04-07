<h1 align="center">heroku-buildpack-wkhtmltopdf</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](/LICENSE)

</div>

## 📝 Table of Contents

- [About](#about)
- [Feature](#feature)
- [Getting Started](#getting_started)
- [Usage](#usage)
- [Acknowledgements](#acknowledgement)
- [License](#license)
- [Changelog](#changelog)


##  About <a name = "about"></a>

This buildpack downloads and extracts the
[wkhtmltopdf](https://wkhtmltopdf.org/) binaries and works on `heroku-18`, `heroku-20` and `heroku-22` stacks.

- This buildpack downloads wkhtmltopdf v0.12.6.1-2 for `heroku-22`, v0.12.6-1 for `heroku-20` stack and v0.12.5 for `heroku-18` stack.
- This buildpack can bypass stack detection if the url to the wkhtmltopdf binary is provided through Aptfile.

## Changelog <a name = "changelog"></a>
- v1.0 (initial release)
  - Support for `Cedar-14`, `heroku-16`,  and `heroku-18`
  - Support for [Aptfile](#aptfile)

- v2
    - Added support for `Heroku-20`
    - Removed support for `Cedar-14` and `heroku-16` as they reached end of life.

- v3
    - Added support for `Heroku-22`
    - Added support for bypassing stack detection.

## Features <a name = "feature"></a>
- Downloads wkhtmltopdf binaries from [wkhtmltopdf.org](http://wkhtmltopdf.org)
- It doesnot add new environment variables or shell scripts.
- Tested on `heroku-22`, `heroku-20` and `heroku-18`stack images.
- It allows you to specify a custom or the latest version of wkhtmltopdf package for your app on Heroku. [Aptfile](#aptfile).

## Getting Started <a name = "getting_started"></a>
Just add the buildpack to your heroku app by executing:

```bash
heroku buildpacks:add https://github.com/RohanDebroy/heroku-buildpack-wkhtmltopdf.git
```

You can also force this buildpack to be the first Heroku process by using the
`--index` option:

```bash
heroku buildpacks:add --index=1 https://github.com/RohanDebroy/heroku-buildpack-wkhtmltopdf.git
```
### Aptfile(Optional) <a name="aptfile"></a>
To use a specific version of the wkhtmltopdf binary for your app on Heroku, you can include an `Aptfile` in the parent directory of your app. This file should contain the latest or custom download URL for the binary.

By including the `Aptfile`, you can bypass Heroku's stack detection and ensure that the correct version of wkhtmltopdf is downloaded during the build process.

Here are the steps to include an Aptfile in your app:

- Create a file named "Aptfile" in the parent directory of your app.
- Add the download URL for the version of wkhtmltopdf that you want to use to the Aptfile.
- Commit the Aptfile to your app's Git repository.
- Push the changes to Heroku.
- Once you've completed these steps, Heroku will use the specified version of wkhtmltopdf during the build process for your app.

### Warning: When using an Aptfile to specify the version of wkhtmltopdf for your app on Heroku, it's important to note that the Aptfile bypasses stack detection. This means that you need to make sure you are using the correct binary version for your Heroku stack.

## Usage <a name="usage"></a>

The binaries `wkhtmltopdf` and `wkhtmltoimage` will be available on `/app/bin`,
you can just execute `/app/bin/wkhtmltopdf ` and `/app/bin/wkhtmltoimage`  from your app.


## Acknowledgements <a name = "acknowledgement"></a>

- All thanks to [heroku-buildpack-apt](https://github.com/ddollar/heroku-buildpack-apt) project.

## License <a name="license"></a>
MIT
