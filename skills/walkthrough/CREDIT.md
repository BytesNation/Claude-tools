# Credit

`template.sh` in this folder is the work of Matt Pocock, taken from
[mattpocock/skills](https://github.com/mattpocock/skills) under the MIT licence.
The full licence text sits beside it in `LICENSE`, and it is the licence that
governs that file.

`template.sh` is vendored byte-identical to upstream, 204 lines, no content
changes. One local change: the file carries the executable bit (upstream
tracks it as `100644`, ours as `100755`), since a shebang script needs it to
run directly. `SKILL.md` is ours, written fresh around it.

To refresh, re-fetch `template.sh` and diff it against upstream before
replacing this copy.
