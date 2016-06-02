# CJK Decomposition Data

The CJK Decomposition Data File is a graphical analysis of the approx
75,000 Chinese/Japanese characters in Unicode.

The data file is in UTF-8 encoding and was originally compiled by
[Gavin Grover](https://www.codeplex.com/site/users/view/gavingrover)
([original project](https://cjkdecomp.codeplex.com/)). It is
distributed under 6 licenses, of which you only need choose one:

- [Apache Licence
  2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

- [LGPL 3.0](http://www.gnu.org/licenses/lgpl.html)

- [Creative Commons BY-SA
  3.0](http://creativecommons.org/licenses/by-sa/3.0/legalcode)

- [MIT license](http://opensource.org/licenses/MIT)

- [Open Data Commons Attribution License (ODC-By)
  v1.0](http://opendatacommons.org/licenses/by/1.0/)

- [Eclipse Public License](http://www.eclipse.org/legal/epl-v10.html)

The data comprises the 36 strokes (`U+31C0..U+31E3`), the 115 radicals
(`U+2E80..U+2EF3`, except `U+2E9A`), the 20,924 unified characters
(`U+4E00..U+9FBB`), the 12 unique characters from the compatibility
range (`U+F900..U+FAD9`), the 6,582 extension A characters
(`U+3400..U+4DB5`), the 42,711 extension B characters
(`U+20000..U+2A6D6`), the 4,149 extension C characters
(`U+2A700..U+2B734`), and the 222 extension D characters
(`U+2B740..U+2B81D`).

Each record has 3 fields, viz, the character being defined, the type
of decomposition, and a list of zero or more constituent components,
like so:

```
的:a(白,勺)
```

The character being defined and the constituent components are either
a Unihan token, in the basic or a supplemental plane, or a 5-digit
number representing an intermediate decomposition not in
Unicode. There are approx 10,000 such intermediate decompositions.

If you need a font, you can use the [Hanazono
font](http://fonts.jp/hanazono/).

Only pictorial configurations are used, not semantic ones. Where
characters have typeface differences I've used the one provided by the
Mainland Chinese contribution to Unicode. When there's more than one
possible configuration, I've selected one only.

The possible configurations and their meanings are:

| Code regex  | Meaning         | Number of possible constituents |
|-------------|-----------------|-----|
| `c`         | component       |   0 |
| `m.*`       | modified in some way, e.g. `me`=equivalent, `msp`=special, `mo`=outline, `ml`=left radical version |   1 |
| `w.*`       | second constituent contained within first in some way, e.g. `w`=within at the center, `wbl`=within at bottom left |   2 |
| `ba|d` | second between first moving across or downwards |   2 |
| `lock`      | components locked together |   2 |
| `s.*`       | first component surrounds second, e.g. `s`=surrounds fully, `str`=surrounds around the top-right |   2 |
| `a`         | flows across    | >=2 |
| `d`         | flows downwards | >=2 |
| `r.*`       | repeats and/or reflects in some way, e.g. `refh`=reflect horizontally, `rot`=rotate 180 degrees, `rrefr`= repeat with a reflection rightwards, `ra`=repeat across, `r3d`=repeat 3 times downwards, `r3tr`=repeat in a triangle, `rst`=repeat surrounding around the top |   1 |

The `s`, `a`, `d`, and `r` codes may be followed by `/t`, `/m`, `/s`,
or `/o`, to show whether the join touches, molds, snaps together, or
overlaps, respectively.

Some more work needs to be done, including reducing the quantity of
intermediate components by removing duplicates, lowering the number of
components in many sequences, reanalysis of decomposition
configurations, and of course quality checking and corrections.

# See also

- [cjkvi/cjkvi-ids](https://github.com/cjkvi/cjkvi-ids) for similar (but
  probably more thorough) composition data in [ideographic description
  sequence](https://en.wikipedia.org/wiki/Chinese_character_description_languages#Ideographic_Description_Sequences)
  format
