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
    sudo tlmgr install collection-fontsrecommended dejavu gentium-tug tex-gyre
    ```

4. Unlike what the [documentation suggests](https://wiki.contextgarden.net/Fonts_in_LuaTeX), the fonts database is _not_ regenerated on the next run of `context`, for whatever reason. Regenerate it manually (perhaps not all of the commands below are strictly necessary, but not enough experimentation has been done to confirm):

    ```
    mtxrun --script fonts --reload
    context --generate
    context --make
    ```

5. Verify the fonts are available. Use the example from https://wiki.contextgarden.net/ConTeXt_distribution%27s_Fonts, copied below:

    ```context
    \definepapersize[sheet][width=16cm,height=11cm]
    \setuppapersize[sheet]
    \setuplayout[topspace=0.5mm,            
                 backspace=0.5mm,
                 header=0pt,
                 headerdistance=0pt,
                 footer=0pt,
                 footerdistance=0pt,
                 width=15cm,
                 height=11cm]
    %
    \setupbodyfont[modern]
    \setupbodyfont[10pt]
    \setupinterlinespace[4ex]
    %
    \starttext

    \startbuffer[line]
    The quick brown fox jumps over the lazy dog
    \stopbuffer

    \startitemize[none,packed]
                                    \item default: \getbuffer[line]\\
    \switchtobodyfont[modern]  \item lmserif: \getbuffer[line]\\
    \switchtobodyfont[modern]  \item \ss lmsans: \getbuffer[line]\\
    \switchtobodyfont[modern]  \item \tt lmmono: \getbuffer[line]\\
    \switchtobodyfont[adventor]     \item adventor: \getbuffer[line]\\
    \switchtobodyfont[bonum]        \item bonum: \getbuffer[line]\\
    \switchtobodyfont[chorus]       \item chorus: \getbuffer[line]\\
    \switchtobodyfont[cursor]       \item cursor: \getbuffer[line]\\
    \switchtobodyfont[pagella]      \item pagella: \getbuffer[line]\\
    \switchtobodyfont[pagella]      \item \ss pagella: \getbuffer[line]\\
    \switchtobodyfont[schola]        \item schola: \getbuffer[line]\\
    \switchtobodyfont[termes]       \item termes: \getbuffer[line]\\
    \switchtobodyfont[dejavu]       \item dejavuserif: \getbuffer[line]\\
    \switchtobodyfont[dejavu]       \item \ss dejavusans: \getbuffer[line]\\
    \switchtobodyfont[dejavu]       \item \tt dejavumono: \getbuffer[line]\\
    \switchtobodyfont[gentium]      \item gentium: \getbuffer[line]\\
    \stopitemize

    \stoptext    
    ```
    
    Verify that the output matches the expected output:
    
    ![image](https://user-images.githubusercontent.com/2456381/116314558-196bde80-a764-11eb-93b8-0c14ae5ce2af.png)
