# Sortindexes for Color Sorting

> [!NOTE] 
> **What's a sortindex?**
>
> The sortindex is a hexadecimal number inside a BodyShop package's Binary Index (BINX) resource. It determines the order that BodyShop, CAS, and in-game menus display BodyShop items. It is editable in both SimPE or in the [Outfit Organizer](https://www.picknmixmods.com/Sims2/Notes/OutfitOrganiser/OutfitOrganiser.html) (use the Sort field; press Enter to make the change stick).

> [!IMPORTANT] 
> **Sort Order**
>
> A higher sortindex will show up *earlier* in the catalog. You can think of sortindexes as counting down instead of up.
> All items in a given product (expansion pack / BSOK or CCCASOK group) will sort together, with higher sortindexes earlier within the product.

SSC achieves color sorting (and color palette sub-sorting) by setting the sortindex of each item of clothing.

Sortindexes for SSC clothing are 0x0000[2-digit color code][2-digit palette code]. In the Outfit Organizer, you'll need to supply the [decimal value](https://www.rapidtables.com/convert/number/hex-to-decimal.html).

**Examples**: 
- Neon pink clothing would have a sortindex of 0x0000**90***60*. The decimal value is 36960.
- Pastel blue clothing would have a sortindex of 0x0000**e0***c0*. The decimal value is 57536.


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
| Tints (Pastels) | c0 |
| Tones (Muted) | a0 |
| Shades | 80 |
| Neons | 60 |


