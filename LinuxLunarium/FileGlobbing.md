# File Globbing

Globbing lets you reference files without typing them all out, or typing out their full paths.

## Matching with *

This level taught about the `*` glob. The `*` matches any part of the filename except for / or a leading . character.

For the flag on this level I ran the `cd /ch*` command which moved me to the challenge directory and then ran the `/challenge/run` command to secure the flag.

Flag: pwn.college{AAzvm1SPDcc-viMTaIGPHg4FxXu.dFjM4QDL0IzN0czW}

## Matching with ?

When the shell encounters `?`, it treats it as a single character wildcard.

The following commands gave me the flag.
1. `cd /?ha??enge`
2. `/challenge/run`

Flag: pwn.college{cy88UZvQU-bCq1p5G_eqw_lHP9K.dJjM4QDL0IzN0czW}

## Matching with []

`[]` is a wildcard for some subset of potential characters, specified within the brackets.

I used `/challenge/files` to change my cwd and then `/challenge/run file_[bash]` for the flag.
Flag: pwn.college{0e6K0YyiumYR9acGEPZCV3HwQZk.dNjM4QDL0IzN0czW}

## Matching paths with []

Flag was obtained after running the `/challenge/run` with a single argument `/challenge/files/file_[bash]`
Flag: pwn.college{E9LyGlNlxLpLXfOm9yFrBk6AASF.dRjM4QDL0IzN0czW}

## Mixing Globs

I run `cd /challenge/files` to change my cwd.

The argument had to less than or equal to 6 characters So I ran `/challenge/run [cep]*` to the flag.
Flag: pwn.college{YKljMmWIqBM5xeQUyjvalGhHW3a.dVjM4QDL0IzN0czW}

## Exclusionary globbing

`!` lets you want to filter out files in a glob.
For the flag on this level, I changed my cwd to `/challenge/files` and then ran the `/challenge/run [!pwn]*`
Flag: pwn.college{4vAKN3-h8bDYtWBTZF5eaG4P5Ut.dZjM4QDL0IzN0czW}