# Adding a new BSOK group for CCCASOK

Technically, all you need to do to "create" a new BSOK group is to pick a Product ID and start editing it into your Property Sets. However, there are a few steps you'll probably want to follw in order to add an icon and configure the [BSOK Editor](https://www.picknmixmods.com/Sims2/Notes/BsokEditor/BsokEditor.html) to use your new group.

## Pick a Product ID
You'll want to pick a Product ID with two qualities:
- It should use only the last 4 hexits available. Even though the Product ID is an 8-hexit number, the first four hexits should all be 0.
- It shouldn't be a product ID that a public BSOK scheme is already using. The easiest way I know to see what IDs are in use is just to download the [BSOK Editor](https://www.picknmixmods.com/Sims2/Notes/BsokEditor/BsokEditor.html) and look through the XML files included there. As of v2.4, my advice would be to avoid these prefixes for your four-hexit number:
	- 0x0D and 0x0C (in use by nuBSOK)
	- 0xF, 0xE, 0xD, 0xC, 0xB, 0xA, 0x7, 0x6 (in use by mfBSOK)
	- 0x00, 0x06, 0x07 (in use by legacy BSOK)

[CCCASOK](https://lavenderlight.tumblr.com/post/641985485922795520/the-coordinated-closet-create-a-sim-organisation) currently uses the `0xCA5` and `0xCAF` prefixes. The `0xCAF` prefix overlaps with the mfBSOK Classic Pinup group. This usually doesn't cause a problem because most people won't play a game that includes both a wide range of Medieval content and a wide range of modern Maxis-bodyshape content (which is what CCCASOK was created for), so they'll never encounter the conflict.

> [!NOTE]
> SSC's expansions to CCCASOK use the `0xCAA` prefix, which currently has no collisions recorded in the BSOK Editor's XML files.

You don't need to put the product ID in a .package, but you should write it down somewhere.

## Associate an Icon

You'll need a 16px x 16px image to use as your icon.

1. Open the CCCASOK file and extract one of the resources there.
1. Create a new file and add the extracted resource.
1. Click the new resource and go to it's Resource tab. Change the instance number to be 0xABBB[your four-hexit number].
1. Now change the instance number again to subtract 1 from it. [Here's](https://www.calculator.net/hex-calculator.html?number1=CAAA&c2op=-&number2=1&calctype=op&x=Calculate) a hexadecimal calculator if you're not comfortable doing that yourself.
1. Commit.
1. Right-click the resource and choose Replace. Navigate to your icon and select it. Accept SimPE's offer to reload the resource.
1. Save.
1. Put this file in your Downloads folder.

> [!NOTE]
> The 0xABBB prefix requirement for the icon ID number is largely why your Product ID should be only four hexits long.

## Update your Personal BSOK Editor

This is not necessary to make the game see your new group, but it will help a great deal in assigning outfits to it!

1. Find where your BSOK Editor files live. Open the Resource/XML/bsok_05cccasok.xml file.
1. Add this line to the file, right after the last `<role>` line:

```
<role name="Your Group Name" code="0x0000[your 4-digit hexit number]"/>
```

> [!NOTE]
> If you're planning to distribute your new group as something else other people will use, you should contact both [lavenderlight](https://lavenderlight.tumblr.com/) (CCCASOK originator) and [Pick'N'Mix Sims](https://www.picknmixmods.com/Sims2/Main/About.html) (BSOK Editor developer) to give them a heads up. If you know what "pull request" means, it's probably kind to send a pull request to update the [CCCASOK XML file](https://github.com/whoward69/Sims2Tools/tree/main/BsokEditor/Resources/XML) as well.