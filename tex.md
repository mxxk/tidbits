# TeX Tidbits

## Expansion

### `\expandafter`

The following is a high-level (possibly not entirely accurate) model of how TeX `\expandafter` works.

An important realization in learning TeX expansion is the difference between expansion and execution/actions (an expansion is merely a transformation of an input sequence of TeX tokens into an output sequence of tokens). This point is covered in Part 5 of the excellent article series on `\expandafter` on Overleaf: [How does \expandafter work: A detailed macro case study](https://www.overleaf.com/learn/latex/Articles/How_does_%5Cexpandafter_work:_A_detailed_macro_case_study).



1. Initial expression

    ```
    \ea1\ea2\ea3\a\ea4\b\c
    ```

2. `\ea1` expanded

    1. `\ea2` saved

    2. `\ea3` expanded

        1. `\a` saved

        2. `\ea4` expanded

            - `\b` saved

            - `\c` expanded

3. Expression after previous expansion:

    ```
    \ea2\a\b<expansion of \c>
    ```

4. `\ea2` expanded

    a. `\a` saved

    b. `\b` expanded

5. Expression after previous expansion:

    ```
    \a<expansion of \b><expansion of \c>
    ```

6. `\a` expanded

7. Expression after previous expansion:

    ```
    <expansion of \a><expansion of \b><expansion of \c>
    ```
