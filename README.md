A simple Jekyll page which can have lots of posts currated to be of interest to DoD developers.


# Bulding

Because rebuilding Bootstrap every time is slow and Jekyll seems to want to rebuild it every time, we've moved to just building it manually when needed for faster development. To build, remove the exclude in `_config.yml` and cp the resulting `_site/css/bootstrap.css' to `css/bootstrap.css`.
