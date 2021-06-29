<h1 align="center">heroku-buildpack-wkhtmltopdf</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](/LICENSE)

</div>

---


## 📝 Table of Contents

- [About](#about)
- [Feature](#feature)
- [Getting Started](#getting_started)
- [Deployment](#deployment)
- [Usage](#usage)
- [Acknowledgements](#acknowledgement)
- [License](#license)
- [Changelog](#changelog)


##  About <a name = "about"></a>

This buildpack downloads and extracts the most recent
[wkhtmltopdf](https://wkhtmltopdf.org/) binaries and works on `heroku-18` and `heroku-20` stacks.

- This buildpack downloads wkhtmltopdf v0.12.6-1 for `heroku-20` stack and v0.12.5 for `heroku-18` stack.
- This buildpack may support future wkhtmltopdf binary releases(not tested yet) through Aptfile. 

## Changelog <a name = "changelog"></a>
- v1.0 (initial release)
  - Support for `Cedar-14`, `heroku-16`,  and `heroku-18`
  - Support for [Aptfile](#aptfile)

- v2
    - Added support for `Heroku-20`
    - Removed support for `Cedar-14` and `heroku-16` as they reached end of life.

## Features <a name = "feature"></a>
- Downloads wkhtmltopdf binaries from [wkhtmltopdf.org](http://wkhtmltopdf.org)
- It doesnot add new environment variables or shell scripts.
- Tested on both `heroku-20` and `heroku-18`stack images.
- Added ability to specify custom or latest wkhtmltopdf package through [Aptfile](#aptfile) (Not Tested).

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
The <b>Aptfile</b> can be included in the parent directory of you app. If you add the latest or custom wkhtmltopdf binary download url to the aptfile as described below then the buildpack can download the version for you and it in to /app/bin folder of heroku.

    #filename should be "Aptfile" without quotes.
    # you can include links to specific .deb files or .tar.xz
    https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6-1/wkhtmltox_0.12.6-1.focal_amd64.deb
    

## Usage <a name="usage"></a>

The binaries `wkhtmltopdf` and `wkhtmltoimage` will be available on `/app/bin`,
you can just execute `/app/bin/wkhtmltopdf ` and `/app/bin/wkhtmltoimage`  from your app.


## Acknowledgements <a name = "acknowledgement"></a>

- All thanks to [heroku-buildpack-apt](https://github.com/ddollar/heroku-buildpack-apt) project.
- Forgive me if I've used your code and forgot to mention you.

## License <a name="license"></a>
MIT
