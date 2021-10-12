# PDF Tidbits

## Invert PDF Colors

(Useful for PDF "darkmode".)

1. Start a Docker container with a bind volume mount to the current directory:

    ```
    docker run --rm -it -v "$PWD:/mnt" alpine
    ```

2. Install Ghostscript within the container:

    ```
    apk add --no-cache ghostscript
    ```

3. Invert colors on the desired PDF:

    ```
    gs -o /mnt/input.pdf \
       -sDEVICE=pdfwrite \
       -c '{1 exch sub}{1 exch sub}{1 exch sub}{1 exch sub} setcolortransfer' \
       -f /mnt/output.pdf
    ```

_NOTE: Not all PDF viewers will respect this method of inverting PDF colors. See reference below for more information._

Inspired by: https://superuser.com/a/1366655
