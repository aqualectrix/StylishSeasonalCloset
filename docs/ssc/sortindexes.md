# Sortindexes for Color Sorting

> [!NOTE] 
> **What's a sortindex?**
>
> The sortindex is a hexadecimal number inside a BodyShop package's Binary Index (BINX) resource. It determines the order that BodyShop, CAS, and in-game menus display BodyShop items. It is editable in both SimPE.

> [!IMPORTANT] 
> **Sort Order**
>
> A higher sortindex will show up *earlier* in the catalog for things the game recognizes as custom content. For things the game recognizes as part of an expansion or stuff pack -- even fake ones like CCCASOK groups -- a higher sortindex will show up *later* in the catalog.
> All items in a given product (expansion pack / BSOK or CCCASOK group) will sort together, with lower sortindexes earlier within the product.

SSC achieves color sorting (and color palette sub-sorting) by setting the sortindex of each item of clothing.

Sortindexes for SSC clothing are 0x0000[2-digit color code][2-digit palette code].

**Examples**: 
- Neon pink clothing would have a sortindex of 0x0000**70***90*.
- Pastel blue clothing would have a sortindex of 0x0000**20***30*.


Color codes:
| Color | Color Code |
| --- | --- |
| Black | 10 |
| Blue | 20 |
| Brown | 30 |
| Green | 40 |
| Grey | 50 |
| Orange | 60 |
| Pink | 70 |
| Purple | 80 |
| Red | 90 |
| Turquoise | a0 |
| White | b0 |
| Yellow | c0 |

Palette codes:
| Palette | Palette Code |
| --- | --- |
| Pure | 10 |
| Tints (Pastels) | 30 |
| Tones (Muted) | 50 |
| Shades | 70 |
| Neons | 90 |


