# ConTeXt Tidbits

## Minimal-ish Installation on MacOS

1. Since the full TeX Live distribution can be heavy, install BasicTeX.

    ```
    brew install basictex
    ```

2. Install ConTeXt

    ```
    sudo tlmgr install context
    ```

3. Install fonts which are supposed to be distributed with ConTeXt (https://wiki.contextgarden.net/Use_fonts_distributed_with_ConTeXt), but were not installed due to the use of BasicTeX above:

    ```
    sudo tlmgr install collection-fontsrecommended dejavu gentium-tug
    ```

4. Unlike what the [documentation suggests](https://wiki.contextgarden.net/Fonts_in_LuaTeX), the fonts database is _not_ regenerated on the next run of `context`, for whatever reason. Regenerate it manually (perhaps not all of the commands below are strictly necessary, but not enough experimentation has been done to confirm):

    ```
    mtxrun --script fonts --reload
    context --generate
    context --make
    ```
