[<img align="right" src="examples/python_snake.gif?raw=true">](examples/python_snake.py)

# glc.py

This is a Python library made to help with the creation of code-based animation.
Heavily based on (honestly, it could be considered a "port" of) [gifloopcoder][glc] by [bit101][kp].

The documentation can be found [here](http://glcpy.readthedocs.io/en/latest/).

This uses [pycairo][pyc] for drawing. You can also use [cairocffi][ccf], which is mostly compatible with [pycairo][pyc].
To do so, add the following at the top of your script:

```py
try:
    import cairocffi
    cairocffi.install_as_pycairo()
    print("using cairocffi")
except ImportError:
    print("using pycairo")
```

## Installing

As this library is not on PyPI, you'll need to do something like:

```
pip install git+https://github.com/leovoel/glc.py
```

See "Requirements" on necessary info for the dependencies of this lib.

## Tiny Example

```py
import glc

with glc.Gif("a_circle.gif", w=500, h=500) as a:
    l, w, h = a.render_list, a.w, a.h
    l.circle(x=w * 0.5, y=h * 0.5, radius=[100, 200])
```

## Requirements

- [pycairo][pyc]/[cairocffi][ccf]
- [imageio][iio]
- [Pillow][pil]
- [numpy][npy]
- [Python 3+][py]

Normally, `imageio` and `numpy` should be installed when you use `pip` to install the lib.

You'll need to install pycairo/cairocffi and Pillow on your own.

If you're on Linux or OSX, you can try using [this](https://github.com/ldo/pycairo/) (using `pip install ...`).
Otherwise, you'll have to build it yourself.

If you're on Windows, you can use [this page](http://www.lfd.uci.edu/~gohlke/pythonlibs/),
which contains pre-built binaries for a ton of libraries, including pycairo.

If you want to have support for transparent gif exporting, you'll also need to install [ImageMagick][imck].
After installing it, set the `IMAGEMAGICK_BINARY` environmental variable to point to the `convert` application that is part of ImageMagick.

On Windows, it's usually something like this:

```
C:\Program Files\ImageMagick-VERSION_NUMBER\convert.exe
```

You'll also need [FFmpeg][ffmpeg] if you want to export using ImageMagick without creating temporary files.

To specify what converter should be used, pass `converter="imagemagick"` or `converter="imageio"`
in the constructor for a `Gif`, like so:

```py
with Gif("hey.gif", converter="imageio") as a:
    ...
```

The default is to use imageio.

[py]: https://www.python.org/
[glc]: https://github.com/bit101/gifloopcoder/
[kp]: https://github.com/bit101/
[pyc]: http://www.cairographics.org/pycairo/
[ccf]: https://github.com/SimonSapin/cairocffi
[imck]: http://imagemagick.org/script/index.php
[iio]: https://github.com/imageio/imageio
[pil]: https://github.com/python-pillow/Pillow
[npy]: http://www.numpy.org/
[ffmpeg]: http://ffmpeg.org/
