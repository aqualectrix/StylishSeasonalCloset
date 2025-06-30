# Sortindexes for Color Sorting

> [!NOTE] What's a sortindex?
>
> The sortindex is a hexadecimal number inside a BodyShop package's Binary Index (BINX) resource. It determines the order that BodyShop, CAS, and in-game menus display BodyShop items.

> [!IMPORTANT] Sort Order
>
> A higher sortindex will show up *earlier* in the catalog. You can think of sortindexes as counting down instead of up.
> All items in a given product (expansion pack / BSOK or CCCASOK group) will sort together, with higher sortindexes earlier within the product.

SSC achieves color sorting (and color palette sub-sorting) by setting the sortindex of each item of clothing.

Sortindexes for SSC clothing are 0x0000[2-digit color code][2-digit palette code].

Color codes:
| Color | Color Code |
| --- | --- |
| Black | f0 |
| Blue | e0 |
| Brown | d0 |
| Green | c0 |
| Grey | b0 |
| Orange | a0 |
| Pink | 90 |
| Purple | 80 |
| Red | 70 |
| Turquoise | 60 |
| White | 50 |
| Yellow | 40 |

Palette codes:
| Palette | Palette Code |
| --- | --- |
| Pure | e0 |
| Tints | c0 |
| Tones | a0 |
| Shades | 80 |
| Neons | 60 |


