# Default Replace a Maxis Outfit with a Different Maxis Outfit

This is used to create seasonal alternatives for Maxis clothing in SSC.

Here's the bare bones of replacing the Original outfit with the Replacer outfit:

## Extract Resources from the Original
Once you [know the Original outfit's name](maxisfindname.md), e.g. `aftophalter_dots` or just `aftophalter`:

1. Use the SimPE Finder to do a **PropertySet Search** for the name of the Original.
1. Double-click the found property set in the latest expansion pack that includes it. This opens the appropriate Skins.package with that property set selected.
1. Sort by Instance.
1. Extract the GZPS resource with the name you searched for.
1. Extract the 3IDR resource with the matching Instance number.

If the Finder doesn't work, manually open the appropriate Skins.package (which lives inside the expansion/stuff pack's `TSData/Res/Catalog/Skins folder`), sort by name, scroll until you find the Original's name, select it. Then sort by Instance to find the matching 3IDR.

## Add Resources To New Package
1. Create a new package in SimPE. This is your default replacement file.
1. Add the 3IDR and GZPS you extracted from the original. Save.
1. In the 3IDR resource, note:
  - The order of the resources. Typically this is "Resource Node, Shape, Material Definition".
  - The number unique Material Definition lines. This is the "number of groups" and you'll have to do some extra work later if your Original and Replacer don't have the same number. Sometimes Maxis 3IDRs will have duplicate lines -- you only care about the first unique set of lines.
1. Remove all this stuff, leaving the 3IDR empty -- don't delete the resource itself, though. Commit and Save.

## Extract Mesh Resources from the Replacer
> [!IMPORTANT]
> Ignore this step if doing a texture-only replacer.

Once you [know the Replacer outfit's name](maxisfindname.md), e.g. `aftophalter_dots` or just `aftophalter`: 
1. Use the SimPE Finder to do a **NameMap Search** for the name of the Replacer -- just the mesh part of the name. E.g., if your replacer is `aftopmomshirt_pink`, search for only `aftopmomshirt`.
1. Double-click the found `shpe` resource in the latest expansion pack that includes it. This opens the appropriate package with that resource selected.
1. Extract the SHPE resource with the name you searched for.
1. Back to the Finder. Double-click the found `cres` resource in the latest expansion pack that includes it.
1. Extract the the CRES resource with the name you searched for.
1. Look at the GMDC resource. Check how many unique names are listed in the model panel. This is the "number of groups" -- compare it to the number of groups you found in the Original and note if they're different.

## Reference the Replacer Mesh Resources
> [!IMPORTANT]
> Ignore this step if doing a texture-only replacer.

1. Open your default replacement file.
1. Add the CRES and SHPE resources you extracted from the Replacer. Save.
1. Open the 3IDR resource. Click the "Package" button in the Plugin View.
1. From the window that pops up, drag the Resource Node (CRES) and then the Shape (SHPE) lines into the empty 3DIR area. **Order is important** -- use the "up" and "down" buttons if necessary to make sure these lines are in the same order they were in the Original. (Usually that's Resource Node, then Shape.)
1. Commit and Save.
1. Delete the CRES and SHPE resources; we only needed them temporarily. Save.

## Extract Texture Resources from the Replacer
> [!IMPORTANT]
> Ignore this step if doing a mesh-only replacer.

Once you [know the Replacer outfit's name](maxisfindname.md), e.g. `aftophalter_dots`: 
1. Use the SimPE Finder to do a **NameMap Search** for the full name of the Replacer.
1. Double-click the found `txmt` resource in the latest expansion pack that includes it. This opens the appropriate package with that resource selected.
1. Extract the TXMT (Material Definition) resource. 
1. If the Replacer has multiple groups, repeat for each TXMT resources.

## Reference the Replacer Texture Resources
> [!IMPORTANT]
> Ignore this step if doing a mesh-only replacer.

1. Open your default replacement file.
1. Add all the TXMT resources you extracted from the Replacer. Save.

### Single TXMT
1. Open the 3IDR resource. Click the "Package" button in the Plugin View.
1. From the window that pops up, drag the Material Definition line into the 3DIR area. **Order is important** -- use the "up" and "down" buttons if necessary to make sure this line are in the same order they were in the Original. (Usually the Material Definition is after the Resource Node and Shape lines.) 
1. Commit and Save.

### Multiple TXMTs
1. Open the GZPS (Property Set) resource. You're looking for the line called `override0subset`If there are lines with 1, 2, 3, etc. in them instead of 0 (e.g. `override1subset`), you care about those too.
1. Write down the subset names in order. For example, you might note "0: bottom, 1: extra".
1. In SimPE's Resource List, look at the names of the TXMT (Material Definition) resources. Usually they have the form "##numbersandletters!groupname_txmt". Match each group name to the notes you've already taken and also note down the instance number for that group. If there are more TXMTs than overridesubset lines, note down the additional group names and instance numbers.
1. Open the 3IDR resource. Click the "Package" button in the Plugin View.
1. From the window that pops up, drag the Material Definition lines into the empty 3DIR area. **Order is important** -- use the "up" and "down" buttons if necessary to make sure these lines are in the same order as they are in your notes. Check that the last section of each Material Definition in the 3IDR window matches the instance numbers you noted down in the order you noted them down. Typically all Material Definition lines should be below the Shape line. 
1. Commit and Save.

Finally, delete all the TXMT resources from your package. We only needed them temporarily. Save.

## Reconcile Overrides
> [!IMPORTANT]
> You only need to do this step if your replacement includes TXMTs **and**:
> - You have a difference in the "number of groups" from the Original and Replacer
> - **or** your TXMTs had different subset names than the subsets you noted in the Property Set (GZPS).

1. Open your default replacement file.
1. Open the Property Set (GZPS) and get your TXTR order / subset name notes.

### Original # of Groups > Replacer # of Groups
If your Original has more overrides ("groups") than your Replacer:
1. Change the `numoverrides` line to match the number of groups in your replacer.
1. Remove any extra `override` lines. For example, if you have only one group, you must remove `override1shape`, `override1subset`, `override1resourcekey`, and any further overrides with numbers greater than 0 in their names.
1. Make sure each `overridesubset` line, in numerical order starting at 0, matches the ordered list of subset names you noted from your TXMTs. 
1. Commit and Save. 

### Original # of Groups == Replacer # of Groups
If your Original has the same number of overrides ("groups") than your Replacer, but different subset names:
1. Change each `overridesubset` line, in order, to match the ordered list of subset names you noted from your TXMTs.
1. Commit and Save.

### Original # of Groups < Replacer # of Groups
If your Original has fewer overrides ("groups") than your Replacer:
1. Change the `numoverrides` line to match the number of groups in your replacer.
1. Make sure each existing `overridesubset` line, in numerical order starting at 0, matches the ordered list of subset names you noted from your TXMTs... until you run out of existing `overridesubset` lines.
1. For each extra group, in the order found in your notes:
	1. Note the highest number currently in the `override` lines. For example, if you only have `override0` lines, the highest number is 0.
	1. Add one to that number to come up with X. In our example, X is 1.
	1. Add a line called `overrideXshape`, where X is your number from the previous step. This line has the `dtUInteger` type, and its value is 0.
	1. Add a line called `overrideXsubset`, where X is your number. This line has the `dtString` type, and its value is the next subset name on your list that doesn't have overrides configured yet.
	1. Add a line called `overrideXresource`, where X is your number. This line has the `dtUInteger` type, and its value is one greater than the highest existing `overrideresource` value. For example, if our highest existing line is `override0resource (dtUInteger) = 0x00000002`, our new line would be `override1resource (dtUInteger) = 0x00000003`.
	1. Commit and Save. Repeat for each extra group.

## Edit the Property Set
If you're happy with the ages, genders, categories, name, and shoe sounds of the Original, **and you did not need to reconcile any overrides**, you can simply delete the Property Set (GZPS) resource from your package.

If you're happy with all that **but you reconciled overrides**, you need to keep the Property Set resource in your package but you don't need to edit it.

If you want to change ages, genders, categories, name, or shoe sounds, do so in your preferred program (SimPE, Wardrobe Wrangler, Outfit Organizer, etc.).